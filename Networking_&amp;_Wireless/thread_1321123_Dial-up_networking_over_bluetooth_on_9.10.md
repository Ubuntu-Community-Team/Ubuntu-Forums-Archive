---
title: "Dial-up networking over bluetooth on 9.10"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by heroicslug on 2009-11-09
Okay, so here's my problem. I just installed 9.10 on my Lenovo s10 netbook.. I installed the bluetooth module a few months back and want to be able to use my LGVX10000 as a modem, like I do in Windows. I can get the computer to recognise the phone, but there is no option to dial. Is it possible to make this work, or am I just gonna have to use the USB cable on this one?

---

### Post by Heero_Yuy_X on 2009-11-29
sorry for the late reply, I discovered a solution just a short while ago... :D

> Install blueman "sudo aptitude install blueman"
> Open blueman from System -> Preferences -> Bluetooth Manager
> Search and pair your phone, then right click Serial Ports -> Dialup Service
> Now go to Preferences -> Network Connections, choose Mobile Broadband then Add
> You should see some number indicating a connected device, this is your phone, now go through the wizard to setup your APN and cell network options and then you're done!

Hope this helps ;)

---

### Post by [A]madeus on 2009-11-30
Thank you.

---

