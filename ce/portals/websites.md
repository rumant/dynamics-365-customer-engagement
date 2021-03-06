---
title: "Create and manage websites in Dynamics 365 Portal | MicrosoftDocs"
description: "Learn how to create and manage websites in Dynamics 365 Portal."
ms.custom:
  - dyn365-portal
ms.date: 06/20/2018
ms.service: dynamics-365-customerservice
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: article
ms.assetid: 0CF45CAC-4643-46AA-93C0-2D5C97497AEE
ms.reviewer: ""
author: sbmjais
ms.author: shjais
manager: sakudes
---

# Create and manage websites

A website is the core entity of [!INCLUDE[pn-dynamics-crm](../includes/pn-dynamics-crm.md)] Portal application. A portal application selects a single Website record, and this determines what portal entities – [web pages](web-page.md), [web files](web-files.md), [web roles](create-web-roles.md), [content snippets](customize-content-snippets.md), etc. – are applicable to this application.

With a website providing an application scope, multiple distinct portal applications can be connected to a single [!INCLUDE[pn-dynamics-crm](../includes/pn-dynamics-crm.md)] organization.

> [!NOTE]
> Determination of which website record a given portal application is bound to is usually by the website's name, specified in the configuration of the portal deployment.
However, it is also possible to control this by URL path prefix (see the descriptions of Parent Website and Partial URL under [website attributes](#website-attributes)), or by domain, using website bindings.

## Manage websites

Websites can be created, edited, and deleted within [!INCLUDE[pn-dynamics-crm](../includes/pn-dynamics-crm.md)]. 

> [!WARNING]
> When deleting a website record, the portal entities related to the website (web pages, web files, etc.) will also be deleted. This is generally the desired behavior, as it means an entire website and all its related data can be removed from a [!INCLUDE[pn-dynamics-crm](../includes/pn-dynamics-crm.md)] organization in a single operation.

1. Sign in to [!INCLUDE[pn-dynamics-crm](../includes/pn-dynamics-crm.md)].

2. Go to **Portals** > **Websites**.

3. To create a new website, select **New**.

4. To edit an existing website, select the website name.

5. Enter appropriate values in the fields.

6. Select **Save & Close**.

### Website attributes

|Name|Description|
|-----|----------|
|Name|The descriptive name of the website. This field is required.|
|Parent Website|The parent website of the website. This field can generally be ignored, except in certain advanced portal configurations in which a single portal application is bound to one "master" website at the application root path, with one or more "child" websites available at specific sub-paths.|
|Partial URL|The root URL path segment for all URLs generated for portal entities related to this website.<br>For example, if a portal application is deployed to be available at the root of the domain example.com, and this attribute has no value, a request to `http://example.com/` will render the Home web page of the application website (as the Home web page is required to have its Partial URL set to "/").<br>If this attribute is set to the value "my-website", the Home Web Page will instead have a URL of `http://example.com/my-website/`, and all pages in the website will have the same "/my-website/" path prefix.<br>In most portal configurations, this field can be ignored and left blank.<br>Partial URL values are used as URL path segments. As such, they should not contain illegal URL path characters, such as "?", "#", "!", "%". Since portal URLs are generated by joining together Partial URL values with slashes ("/"), they should also not generally contain slashes.<br>Recommended practice would be to restrict Partial URL values to letters, numbers, and hyphens or underscores. For example: "press-releases", "Users_Guide", "product1".|
|||

### See also
[Website bindings](website-bindings.md)