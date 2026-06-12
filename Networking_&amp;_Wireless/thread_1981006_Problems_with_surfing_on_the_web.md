---
title: "Problems with surfing on the web"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by airplanesimen on 2012-05-16
Hi!

I got the rt2800pci card in my hp4330s probook from HP. 

The reason i write here, is that my web-browsing isnt normal. I am connected to a WPA-PSK2 network with MASCHAP (..) v0 and i am using network-authentication. (Username and password, containing to a domain).

I cant access most of the https sites, and i was wondering if it wass possible to fix?

---

### Post by airplanesimen on 2012-09-20
Okay, old thread, still no answer.

Let me tell you more about the problem:

When i try to enter google in my web-browsers, the connection in the browser times out and return to me that the page couldnt be loaded. But bing works perefctly well, aswell as Ubuntu forums, and the login page for facebook.

Everywhere i am trying to log in, it doesnt do anything and times out. I am suspecting my network is prohibiting the computer to upload information or something, and is that possible to fix?
here is what i am using on my proxy.

```
Acquire::http::Proxy "http://<DOMAIN>\<USER>:<PASSWORD>@<PROXY-IP>:8080/";
```

And still ask me in the browser about (attachment 1) the username and password.

Attachment 2 is the google page that refuses to load.

The third attachment shows the Facebook page that loads, but when i log in it times out. You can see in the bottom left corner in the browser, it says "uploading: 0%".

Any ideas what the problem might be?

I will be so happy if this could be fixed, because i really need ubuntu, and its pretty important to fix this! Thanks!

---

### Post by airplanesimen on 2012-09-24
Please, isnt there anyone who could have tried to help me?

Thanks :/

---

### Post by airplanesimen on 2012-09-25
This is hopeless..

---

### Post by jon zendatta on 2012-09-25
have you tried enable/disable IPV6?
[http://www.upubuntu.com/2012/06/how-to-enabledisable-ipv6-in-google.html]("http://www.upubuntu.com/2012/06/how-to-enabledisable-ipv6-in-google.html"):KS

---

### Post by airplanesimen on 2012-09-25
> **jon zendatta said:**
> have you tried enable/disable IPV6?
[http://www.upubuntu.com/2012/06/how-to-enabledisable-ipv6-in-google.html]("http://www.upubuntu.com/2012/06/how-to-enabledisable-ipv6-in-google.html"):KS

Sorry, the link you sent me was broken (The blog you entered doesnt exist!) - Error message :/ But i will try that thankyou, i got a clue of what i should do ^^ If not, i will PM you :P:KS

---

### Post by airplanesimen on 2012-09-25
> **jon zendatta said:**
> have you tried enable/disable IPV6?
[http://www.upubuntu.com/2012/06/how-to-enabledisable-ipv6-in-google.html](http://www.upubuntu.com/2012/06/how-to-enabledisable-ipv6-in-google.html):KS
The Ipv6 was already disabled. Any other suggestions? It fails to load in multiple browsers ( only a few websites)

---

### Post by windscape on 2012-09-25
Hi,

You probably need to define a https proxy as well. Add another proxy statement and change http to https.

---

### Post by airplanesimen on 2012-09-25
aha, okay, that could maybe explain more.. Soo, in the apt.conf file, i should have both

```
Acquire::http::Proxy "http://<DOMAIN>\<USER>:<PASSWORD>@<PROXY-IP>:8080/";
Acquire::https::Proxy "http://<DOMAIN>\<USER>:<PASSWORD>@<PROXY-IP>:8080/";
```
?? 

Thanks again!

---

### Post by windscape on 2012-09-25
Hi,

Yes, that looks right.

Also, that might just help you to download packages using apt-get or the Ubuntu Software Center. Your browser probably has separate proxy settings that also need to be configured either in the browser itself (both for HTTP and SSL aka HTTPS) or somewhere like the Network Settings.

---

### Post by airplanesimen on 2012-09-26
I know firefox as an example yes, but is this necessary in Chrome?

---

### Post by airplanesimen on 2012-09-26
> **windscape said:**
> Hi,

Yes, that looks right.

Also, that might just help you to download packages using apt-get or the Ubuntu Software Center. Your browser probably has separate proxy settings that also need to be configured either in the browser itself (both for HTTP and SSL aka HTTPS) or somewhere like the Network Settings.

Thanks alot! After defining both http and https in the apt.conf file, all pages loads and i can now surf the web normally. Even though i waited for 3 months, i am so glad someone helped me!


~Regards!

---

