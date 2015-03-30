# Introduction

The RDF to HTML services **RDF2HTML** generate an **HTML** representation of the input **RDF**.

The input **RDF/XML** is transformed using a set of **XSLTs**:
 
* **RDF2HTML**: the simples XSLT, it generates HTML so human users can easily see what the RDF data is about.
* **RDF2HTML+RDFa**: in addition to HTML for humans, hidden RDFa is added to keep the original RDF for machines consumption.
* **RDF2RDFa**: this transformation generates just RDFa, without any visible representation for human users. Used by [http://www.ebusiness-unibw.org/tools/rdf2rdfa/]() to generate cut&paset RDFa to enrich existing HTML pages.
* **RDF2Microdata**: like RDF2RDFa but in this case what is generated is Microdata.

# Installation

To build the deployment **WAR** file using the source code and **Maven**:

    mvn clean package

# Use

When deployed in a local servlet container like Tomcat, the RDF2HTML services will be available at something like **http://localhost:8080/rdf2html/rdf2htmlrdfa** or **http://localhost:8080/rdf2html/rdf2rdfa**

(The service is deployed at **rhizomik.net/redefer-services/rdf2html** and it can be tested from [http://rhizomik.net/redefer/rdf2html-form/]())

It can called using **GET** or **POST**. The former is recommended when the RDF to be transformed is available from a URL, the latter when direct input is provided.

The parameters of the service are:

*   **rdf= RDF/XML | URI**: the RDF/XML to be processed or a URI (content negotiated) where it can be retrieved from.
*   **mode= html | snippet**: defines if the output is a full XHTML page or just a snippet for inclusion in other web pages (default "html").
*   **namespaces= true | false**: defines if the rendered output should show information about properties and resources namespaces or not (default "false").
*   **language= en | es | fr...**: filter literals and labels based on the preferred language (default "en").

Examples using GET and the RDF2HTML service deployed at **rhizomik.net/redefer-services/rdf2html**:

*   **Show the RDF about http://dbpedia.org/resource/RDFa**:
    
    [http://rhizomik.net/redefer-services/rdf2html?rdf=http://dbpedia.org/resource/RDFa&mode=html&namespaces=true&language=en]
    (http://rhizomik.net/redefer-services/rdf2html?rdf=http://dbpedia.org/resource/RDFa&mode=html&namespaces=true&language=en)