---
title: "ThinkPad W500 Wireless connection problem WEP method"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by amorteza on 2011-01-21
Hey! I've been working with ubuntu for a while at school, started to like it and decided to install it on a new hard-drive I bought along with windows 7 and everything was fine expect wireless connection. I installed ubuntu 10.10 (64bit) desktop.

I have a ThinkPad W500, with the following wireless network adapter:


[LIST]
[*]Intel® Ultimate N WiFi Link 5300
[/LIST]
 

now everything is fine. ubuntu manages to find all the networks and such at home the network has WEP authentication protocol, I enter the right password but I keep getting rejected, the same password works fine when im on windows 7. I thought the problem maybe for Netwrok Manager, so I installed WICD but still the same problem. I would truly appreciate if someone could give me some hints. I really really want to get started on ubuntu but without network it is not very much practical.

Thank you before hand :) !

---

### Post by gordintoronto on 2011-01-21
WEP has been broken, you should use WPA.

What is the ssid of the router? One word, all lower case, is preferable...

---

### Post by amorteza on 2011-01-24
The SSID is the same as the network name. its "Maryam".
I can change my security method through. the options are:

WEP - open
WEP - shared
WPA-PSK
WPA-PSK and PWA2-PSK
WPA2-PSK

which one is the best option?

---

### Post by gordintoronto on 2011-01-24
Change the name to maryam and use WPA2-PSK.

---

