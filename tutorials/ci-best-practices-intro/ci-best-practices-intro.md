---

title: Continuous Integration (CI) Best Practices with SAP: Introduction and Navigator
description: Part 1: Introduction and Navigation through the Best Practices Guide
tags: [  tutorial>intermediate, tutorial:type/project ]

---

## Prerequisites  
 - **Proficiency:** Intermediate

## Outline

1. [Introduction and Navigator (this document)](http://go.sap.com/developer/tutorials/ci-best-practices-intro.html)  
2. Continuous Integration and Delivery  
2.1. [CI/CD Practices](http://go.sap.com/developer/tutorials/ci-best-practices-ci-cd.html)  
2.2. [Pipeline Suggestions](http://go.sap.com/developer/tutorials/ci-best-practices-pipelines.html)  
3. CI/CD Landscape - Component Setup  
3.1. [Source Code Versioning System](http://go.sap.com/developer/tutorials/ci-best-practices-scm.html)  
3.2. [Build Scheduler](http://go.sap.com/developer/tutorials/ci-best-practices-build.html)  
3.3. [Artifact Repository](http://go.sap.com/developer/tutorials/ci-best-practices-artifacts.html)  
3.4. [Landscape Configuration](http://go.sap.com/developer/tutorials/ci-best-practices-landscape.html)  
3.5. [CD Pipeline Skeleton](http://go.sap.com/developer/tutorials/ci-best-practices-pipeline-skeleton.html)  
4. CI/CD Process Setup  
4.1. [Generic Project](http://go.sap.com/developer/tutorials/ci-best-practices-generic.html)  
4.2. [Java Web on SAP HANA Cloud Platform](http://go.sap.com/developer/tutorials/ci-best-practices-java-hcp.html)  
4.3. [SAP HANA Extended Application Services (XS), classic model](http://go.sap.com/developer/tutorials/ci-best-practices-xsc.html)  

---


An efficient software development process is vital for success in building business applications on SAP cloud
or on-premise platforms.

This guide discusses some basic principles for software development that are derived from the process definitions for
Continuous Integration (CI) and Continuous Delivery (CD). We provide best practices
to support establishing your application development processes especially for SAP HANA Cloud
Platform (SAP HCP) but also for other SAP technologies.

Our customers have requested in-depth guidance for an end-to-end CI process. SAP offers several tools to address single aspects,
such as the WebIDE in HCP.
The goal of this guide is to provide a "big picture" on CI or CD processes and how to give showcases how to set them
up using widely adopted complementary tools. The choice of tools should be considered as examples.
Other tools fulfilling the same purpose will work as well.

We will take a look at the most important SAP technologies and describe how to use existing tools to set up a CI process that
fits the individual needs of your development project, your requirements, and your environment.

Simply follow the step-by-step recipes to set up and configure the technical components. You will learn how to orchestrate those components
to build a generic skeleton CI or CD process that is based on selected SAP technologies. We discuss the specifics
of each technology and explain how to adopt the CI and CD approaches with the help of concrete examples or reference applications.

This guide is intended for any SAP customer or partner who is interested in or currently setting up a development process for
their cloud application development on SAP HCP or on-premise technologies.
The high level principles discussed in part 2 of the guide are intended for a wide audience and will help managers, product owners,
quality managers and developers understand why the principles make sense and how they can be applied.
The subsequent parts are more technical and are intended for the process architects, build engineers, and operators
who are implementing the development process.


## Navigating Through the Best Practices Guide

This best practices guide covers a broad spectrum of aspects and addresses many diverse topics at different levels for people who have
different roles and interests. We have tried to identify some roles and direct them to the sections that are likely to be of
most interest.

### Roles

Role                      | Description, Skill Set
:------------------------ | :----------------------------------------------------------------
Manager, Decision Maker   | Makes investment decisions about infrastructure, tools and usage of public services. Mainly interested in a sustainable investment into the infrastructure.
Quality Manager           | Responsible for product quality. Defines and decides on the processes that ensure the quality level.
Delivery Manager          | Responsible for the shipment and deployment of the product to production. Relies on the quality and defines the deployment process.
Build Operator            | Operates the technical components for a CI/CD infrastructure.
Build Engineer            | Implements the CI/CD process on top of the technical components. Implements and supports the product-specific requirements to be implemented in the build and test procedures. The person in this role might be an expert of the software technology in which the product is implemented. 
Developer engaged in CI   | Implements the build scripts and tests in collaboration with the Build Engineer. An expert of the software technology in which the product is implemented.

### Navigate through the relevant parts of the Guide

+: The part is of interest  
++: The part is of strong interest  
(+): The part is of interest based on the respective technology  
(++): The part is of strong interest based on the respective technology

| Part of the Guide      | Manager, Decision Maker | Quality Manager | Delivery Manager | Build Operator | Build Engineer | Developer engaged in CI |
|-----------|---|---|---|---|---|---|
| **1. [Introduction and Navigator (this document)](http://go.sap.com/developer/tutorials/ci-best-practices-intro.html)** | ++         | ++         | ++         | ++         | ++         | ++          |
| **2. Continuous Integration and Delivery** |            |            |            |            |            |            |
| 2.1. [CI/CD Practices: The Practices and Principles of CI and CD](http://go.sap.com/developer/tutorials/ci-best-practices-ci-cd.html)   | ++         | ++         | ++         | +          | +          | +          |
| 2.2. [Pipeline Suggestions: Patterns for a CI/CD pipeline](http://go.sap.com/developer/tutorials/ci-best-practices-pipelines.html)   | +          | ++         | ++         | +          | ++         |            |
| **3. CI/CD Landscape - Component Setup**   |            |            |            |            |            |            |
| 3.1. [Source Code Versioning System: Setting up a Git/Gerrit Instance](http://go.sap.com/developer/tutorials/ci-best-practices-scm.html)     |            |            |            | ++         |            |            |
| 3.2. [Build Scheduler: Setting up a Jenkins Instance](http://go.sap.com/developer/tutorials/ci-best-practices-build.html)       |            |            |            | ++         |            |            |
| 3.3. [Artifact Repository: Setting up a Nexus Instance](http://go.sap.com/developer/tutorials/ci-best-practices-artifacts.html)       |            |            |            | ++         |            |            |
| 3.4. [Landscape Configuration: Configuring the CI Component Landscape](http://go.sap.com/developer/tutorials/ci-best-practices-landscape.html)       |            |            |            | ++         | +          |            |
| 3.5. [CD Pipeline Skeleton: Setup of a continuous delivery pipeline](http://go.sap.com/developer/tutorials/ci-best-practices-pipeline-skeleton.html)       |            |            |            | ++         | +          |            |
| **4. CI/CD Process Setup**                |            |            |            |            |            |            |
| 4.1. [Generic Project: Configuring the CI system for Maven-based generic Java project](http://go.sap.com/developer/tutorials/ci-best-practices-generic.html)                 |            |            |            | +          | ++         | +          |
| 4.2. [Java Web on SAP HANA Cloud Platform: Configuring the CI system for Maven-based Java Web project](http://go.sap.com/developer/tutorials/ci-best-practices-java-hcp.html) |          |            |            | (+)        | (++)       | (+)        |
| 4.3. [SAP HANA Extended Application Services (XS), classic model: Configuring the CI system](http://go.sap.com/developer/tutorials/ci-best-practices-xsc.html) |          |            |            | (+)        | (++)       | (+)        |
