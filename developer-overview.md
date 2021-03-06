---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Overview for developers
{: #developerOverview}

You can access the capabilities of the {{site.data.keyword.speechtotextshort}} service via a WebSocket interface, an HTTP Representational State Transfer (REST) interface, or an asynchronous HTTP interface. You can also customize the service's language models to suit your domain and environment. Several Software Development Kits (SDKs) are also available to simplify application development in various languages and environments. The service returns all JSON response content in the UTF-8 character set.
{: shortdesc}

## Programming with the service
{: #programming}

[Making a recognition request](/docs/services/speech-to-text/basic-request.html) shows you how to request a basic transcription with each of the service's programming interfaces:

-   [The WebSocket interface](/docs/services/speech-to-text/websockets.html) offers an efficient, low latency, and high throughput implementation over a full-duplex connection.
-   [The HTTP REST interface](/docs/services/speech-to-text/http.html) lets you transcribe audio with or without establishing a session with the service.
-   [The asynchronous HTTP interface](/docs/services/speech-to-text/async.html) provides a non-blocking interface that lets you register a callback URL to receive notifications or poll the service for job status and results.

The interfaces provide the same recognition capabilities, but you might specify the same parameter as a request header, a query parameter, or a parameter of a JSON object depending on the interface and method you use. For a complete list of all available parameters, see the [Parameter summary](/docs/services/speech-to-text/summary.html).

## Customizing the service
{: #custom}

[The customization interface](/docs/services/speech-to-text/custom.html) lets you create custom models to improve the service's speech recognition capabilities:

-   *Custom language models* let you define domain-specific words for a base model. Custom language models expand the service's base vocabulary with terminology specific to domains such as medicine and law.
-   *Custom acoustic models* let you adapt a base model for the acoustic characteristics of your environment and speakers. Custom acoustic models improve the service's ability to recognize speech for specific acoustic characteristics.

You can use a custom language model, a custom acoustic model, or both for speech recognition with any of the service's interfaces.

## Using Software Development Kits
{: #sdks}

The {{site.data.keyword.speechtotextshort}} service supports a number of SDKs to simplify the development of speech applications. The SDKs are available for many popular programming languages and platforms, including Node.js, Java, and Python. For a complete list of SDKs and information about using them, see [{{site.data.keyword.watson}} SDKs](/docs/services/watson/getting-started-sdks.html). All SDKs are available from the [watson-developer-cloud namespace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud){: new_window} on GitHub.

## Learning more about application development
{: #learn}

The {{site.data.keyword.speechtotextshort}} service supports two typical programming models. With *direct interaction*, the client streams audio to the service directly. With *relaying via a proxy*, the client and service exchange all data (requests, audio, and results) through a proxy application that resides in {{site.data.keyword.Bluemix_short}}. With the HTTP interface, you can use either programming model; with the WebSocket interface, you must use direct communication.

For more information about working with {{site.data.keyword.watson}} Developer Cloud services and {{site.data.keyword.Bluemix_notm}}, see the following:

-   For an introduction to working with {{site.data.keyword.watson}} services and {{site.data.keyword.Bluemix_notm}}, see [Getting started with {{site.data.keyword.watson}} and {{site.data.keyword.Bluemix_notm}}](/docs/services/watson/index.html).
-   For a language-independent introduction to developing {{site.data.keyword.watson}} services applications in {{site.data.keyword.Bluemix_notm}}, see [{{site.data.keyword.Bluemix_notm}} development approaches](/docs/services/watson/getting-started-bluemix.html).
-   For information about the two programming models available for developing {{site.data.keyword.watson}} applications, see [Programming models for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-develop.html):
    -   With relaying via a proxy, the client relies on a proxy server that resides in {{site.data.keyword.Bluemix_notm}} to communicate with the service. The client passes all requests through the proxy application. Relaying requests via a proxy relies only on service credentials to authenticate with the service; see [Service credentials for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-credentials.html).
    -   With direct interaction, the client uses the proxy application in {{site.data.keyword.Bluemix_notm}} only to obtain an authentication token for the service. It then communicates directly with the service. Direct interaction uses service credentials only to obtain a token; see [Tokens for authentication](/docs/services/watson/getting-started-tokens.html).

    > **Note:** In some regions, new service instances use {{site.data.keyword.Bluemix}} Identity and Access Management (IAM) tokens instead of service credentials for authentication.
    -   For more information about where the service uses IAM access tokens and how to use them for authentication, see the June 12 and May 15 service updates in the [Release notes](/docs/services/speech-to-text/release-notes.html).
    -   For more information about using access tokens with {{site.data.keyword.watson}} services, see [Authenticating with IAM tokens](/docs/services/watson/getting-started-iam.html).

-   For information about controlling the default request logging that is performed for all {{site.data.keyword.watson}} services, see [Controlling request logging for {{site.data.keyword.watson}} services](/docs/services/watson/getting-started-logging.html).

## Considerations for application development
{: #consider}

Converting speech to text is a difficult problem. Some general things to consider when using the {{site.data.keyword.speechtotextshort}} service in your applications follow:

-   *Speech recognition can be very sensitive to input audio quality.* When you experiment with a demo application or build an application of your own that uses the service, try to ensure that the input audio quality is as good as possible. To obtain the best possible accuracy, use a close, speech-oriented microphone (such as a headset) whenever possible and adjust the microphone settings if necessary. Try to avoid using a laptop's built-in microphone.
-   *Choosing the correct model is important.* For most supported languages, the service supports two models: broadband and narrowband. {{site.data.keyword.IBM}} recommends that you use the broadband model for responsive, real-time applications and the narrowband model for offline decoding of telephone speech.
-   *Conversion of speech to text may not be perfect.* Tremendous progress has been made over the last several years. Today, speech recognition technology is successfully used in many domains and applications. However, in addition to audio quality, speech recognition systems are sensitive to nuances of human speech, such as regional accents and differences in pronunciation, and may not always successfully transcribe audio input.
