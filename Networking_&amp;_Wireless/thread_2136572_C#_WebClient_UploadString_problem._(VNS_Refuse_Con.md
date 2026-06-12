---
title: "C# WebClient UploadString problem. (VNS Refuse Connection)"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by adsnoob on 2013-04-18
So I am writing something in c# currently and having it connect to my server and display the information on my site using:

string url = "https://www.urlhere.com/index.php";
string data = "Message Recieved";
using(WebClient client = new WebClient()) {
client.UploadString(url, data);  
}

But each time the code runs i get the error connection refused. I have tried to port forward and everything but till nothing seems to work. The servers using Apache2 to run my website.

Im pretty stumped right now and would love some help from the pro's :] Please and thank you!

---

