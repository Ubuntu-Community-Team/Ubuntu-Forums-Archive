---
title: "Cannot detect wireless eventhough my iphone does"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by pcminh on 2011-01-22
I use ubuntu 10.10 
My laptop can detect other's wireless from neighbour but my home router's wireless.
My iphone and ipad do detect my home wireless and surf the internet well with correct password
So please help me to detect my wireless. I am a newbie, I have searched topics in forum but can not figure out ( i already tried to install linux-module-... follow as a post but did not work) 
I don't know much information, i tried lspci |grep Wireless and here is the result
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```Thanks

---

### Post by grahammechanical on 2011-01-22
First, if you left click the network manager icon and you see a list of available wireless networks then Ubuntu wireless networking is actually working.

Second, if you cannot see your wireless network in the list, then may be the modem is switched off or not connecting to the ISP.

You say "Detect, " Do you mean connect to? Can you detect your home router's wireless but not connect to it? Is this the problem? If so, what have you done to try to connect?

It is customary to select the wireless network. Ubuntu will then ask you to authenticate the connection. You will need to put in a password. It is not the login password but the wireless key, also called WPA-PSK. It is usually printed on a label stuck on the bottom of the router/modem. Ubuntu will then try to make the connection. If the password is wrong you will be asked again to authenticate. Ubuntu will remember anything that you use to authenticate, even wrong passwords.

Regards.

---

### Post by Terzi on 2011-01-22
I think it's the same problem I have. On startup my usb wireless picks up a bunch of neighbouring routers, but not mine (which is sitting in the same room, and is the automatic connection). Connect to Hidden Wireless Network shows my router in its list and sometimes connects, but not always. It's like my system has a blind spot regarding my wireless router. However, if I leave it alone it picks up the signal from the router after about 10 minutes and automatically connects. I have no idea why this happens, and it seems no-one else does either (now using 10.04, but 9.10 had the same issue).

---

### Post by HouTex on 2011-01-22
I have a similar problem.  I started another thread on it.  One of my WAPs (a Linksys) works fine, but the other one does not (a D-Link).  I can finally connect to it by creating a new wireless network and typing the name of the WAP and then the password key, but the WAP never shows up as an available WAP in the network manager screen.  When I do connect to it, Firefox can't connect to the internet.  But Firefox works fine with the other WAP (a Linksys).  I have Ubuntu 9.1 on a new Dell L13.

---

### Post by pcminh on 2011-01-23
> **grahammechanical said:**
> First, if you left click the network manager icon and you see a list of available wireless networks then Ubuntu wireless networking is actually working.

Second, if you cannot see your wireless network in the list, then may be the modem is switched off or not connecting to the ISP.

You say "Detect, " Do you mean connect to? Can you detect your home router's wireless but not connect to it? Is this the problem? If so, what have you done to try to connect?

It is customary to select the wireless network. Ubuntu will then ask you to authenticate the connection. You will need to put in a password. It is not the login password but the wireless key, also called WPA-PSK. It is usually printed on a label stuck on the bottom of the router/modem. Ubuntu will then try to make the connection. If the password is wrong you will be asked again to authenticate. Ubuntu will remember anything that you use to authenticate, even wrong passwords.

Regards.

I mean I can see my home wireless network. And your post remind me another problem of my ubuntu is that i can not even connect to password-protected-wireless eventhough i entered the right password which work with my iphone and ipad

---

