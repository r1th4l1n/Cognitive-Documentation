<!--
NavPath: Bing Speech API/Speech Recognition/REST API
LinkLabel: Get started in cURL
Url: Speech-api/documentation/GetStarted/GetStarted-cURL
Weight: 80
-->

# Get Started with Bing Speech API in cURL

Exercise Bing Speech Recognition API using cURL to convert spoken audio to text by sending audio to Microsoft’s servers in the cloud. The example below is **bash** commands that demonstrates the use of Microsoft Cognitive Services (formerly Project Oxford) Speech To Text API using **cURL**.

The Speech Recognition web example demonstrates the following features using a wav file or external microphone input:
 * Access token generation
 * Short-form recognition
This example assumes that **cURL** is available in your bash environment.

### Table of Contents
*	[Prerequisites](#Prerequisites)
*	[Step 1: Generate an access token](#Step1)
*	[Step 2: Upload audio binary](#Step2)
*	[Related Topics](#Related)

### <a name="Prerequisites">Prerequisites</a>
* #### Platform requirements
The below example has been developed in **bash**. (Also works in git bash/zsh/etc)

* #### Subscribe to Speech API and get a free trial subscription key
Before creating the example, you must subscribe to Speech API which is part of Microsoft Cognitive Services (previously Project Oxford). For subscription and key management details, see [Subscriptions](https://www.microsoft.com/cognitive-services/en-us/sign-up). Both the primary and secondary key can be used in this tutorial.

### <a name="Step1">Step 1: Generate an access token</a>
1.	Replace **your_subscription_key** with your own subscription key and run the command in **bash**.

    `curl -v -X POST "https://api.cognitive.microsoft.com/sts/v1.0/issueToken" -H "Content-type: application/x-www-form-urlencoded" -d 'grant_type=client_credentials&client_id=your_subscription_key&client_secret=your_subscription_key&scope=https://speech.platform.bing.com'`

2.	Save the the string value of **access_token** in the resonse.
    `{"access_token":"**save_this_token**","token_type":"jwt","expires_in":"600","scope":"https://speech.platform.bing.com"}`


### <a name="Step2">Step 2: Upload the audio binary</a>
1.	Replace **your_instance_id**, **your_request_id**, **your_locale**, **your_device_os** in accordance to your own application; Replace **your_access_token** with the token retrieved from [Step 1](#Step1); Replace **your_wave_file** with the actual wave file and run the command in **bash**.

    `curl -v -X POST "https://speech.platform.bing.com/recognize?scenarios=smd&appid=D4D52672-91D7-4C74-8AD8-42B1D98141A5&locale=your_locale&device.os=your_device_os&version=3.0&format=json&instanceid=your_instance_id&requestid=your_request_id" -H 'Authorization: Bearer your_access_token' -H 'Content-type: audio/wav; codec="audio/pcm"; samplerate=16000' --data-binary @your_wave_file`

2. Parse the Succcessful recognition response or Error response

### <a name="Related">Related Topics</a>
* [Get Started with Bing Speech Recognition in C Sharp for .Net on Windows Desktop](GetStartedCSharpDesktop.md)
* [Get Started with Bing Speech Recognition in C Sharp for .Net on Windows Phone 8.1](GetStartedCSharpWinPhone.md)
* [Get started with Bing Speech Recognition and/or intent in Java on Android](GetStartedJavaAndroid.md)
* [Get started with Bing Speech Recognition and/or intent in JavaScript](GetStartedJS.md)
* [Get started with Bing Speech Recognition and/or intent in Objective C on iOS](Get-Started-ObjectiveC-iOS.md)


For questions, feedback, or suggestions about Microsoft Cognitive Services, feel free to reach out to us directly.

 * Cognitive Services [UserVoice Forum](https://cognitive.uservoice.com/)

###### License

All Microsoft Cognitive Services SDKs and samples are licensed with the MIT License. For more details, see [LICENSE](https://github.com/Microsoft/Cognitive-Speech-STT-JavaScript/blob/master/LICENSE.md).
