---
title: "cURL POST GET HTTP verb error"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by pcho on 2012-04-18
Greetings,
 
I am testing cURL functionality on our web development server.
 
------------------------------------------------
Code:
$param['email'] = $data_signup['email'];
$url = API_URL.'/test_api.php?task=email';
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_TIMEOUT, 100);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, $param);
$x = curl_exec($ch);
curl_close($ch);
-----------------------------------------------
However, I have got the follow error message:
 
405 - HTTP verb used to access this page is not allowed.
The page you are looking for cannot be displayed because an invalid method (HTTP verb) was used to attempt access.
 
Error 139 (net::ERR_TEMPORARILY_THROTTLED): Requests to the server have been temporarily throttled.
 
------------------------------------------------
In case I enter the url in IE, It work.
But the above client module got the error message.
 
I have cURL enabled - UBUNTU 10.04.4 PHP 5.3.6-13 Apache 2.2.20
 
Please help me to solve the issue.
 
Many thanks
Paul

---

