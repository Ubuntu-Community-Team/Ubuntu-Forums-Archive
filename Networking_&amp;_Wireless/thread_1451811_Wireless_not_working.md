---
title: "Wireless not working"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by ubun2warrior on 2010-04-11
I am trying to setup a wifi at home and its not working. I have a Desktop and a laptop. The modem is connected to the desktop. I have cofigured the modem and set up a WEP key for security. I have installed Kubuntu on my laptop. 

When I try to connect to my wifi network, it asks for the wep key (well and good). I entered the WEP Key and the KDE wallet manager asks whether to allow always and I tick the check box so that I don't have to enter the password again. Then it shows configuring network, obtaining IP but suddenly it asks for the WEP Key again and I enter and again it asks for the security key (the passphrase). It asks 2 to 3 times and then it does not connect. 

I have tried many times afresh, but same problem occurs. Please help:confused:

---

### Post by Crafty Kisses on 2010-04-11
Hello,

Can you please give me the results of these commands?
```
lspci
lsusb
lshw -C network
```
That will give me a bit more information your network setup, then I can help you further.

---

