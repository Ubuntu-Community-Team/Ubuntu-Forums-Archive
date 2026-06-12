---
title: "How to setup a wireless adhoc network connection between computer and iPod Touch"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by okayneil on 2010-05-02
Hey everyone, 

I have googled everywhere for this answer and so far had no luck. What I want to do is create a wireless ad-hoc network using my LAN adapter and Wireless adapter. For those of you who don't know what that is, its creating a WiFi hot spot from a cable internet connection. This process is (sadly) [very simple in Windows. ]("http://www.microsoft.com/windowsxp/using/networking/setup/adhoc.mspx")Once the connection is setup you then use a static ip in the iPod Touch to connect. 

I have tried the same similar process in Ubuntu 10.4 but with no luck, I cant get the iPod to use the internet. 

Any ideas?

---

### Post by okayneil on 2010-05-04
Bump

---

### Post by okayneil on 2010-05-04
Someone told me this function might not exist in ubuntu, could this be true?

---

### Post by okayneil on 2010-05-08
Bump

---

### Post by okayneil on 2010-05-15
Bump yet again :(

---

### Post by the_jlx on 2010-05-17
bump

---

### Post by Benedolt on 2010-07-12
Hey all!

It's actually pretty easy. Try this:

1. left click on your network manager tray icon and select "create new wireless network"
2. enter your desired network name
3. select "WEP 64/128-bit key" or "none" as encryption method (others won't work!)
4. enter a 5 or 13 digit password
5. select your network with your ipod/iphone
6. done

The key is the encryption method. Apparently iPods don't support any other encryption than 64/128-bit key WEP.

Kudos to froggydancer on [ubuntuusers.de]("http://forum.ubuntuusers.de/topic/ubuntu-als-wlan-gateway-router-bridge/?highlight=ad#post-2307506") who found this solution!

---

