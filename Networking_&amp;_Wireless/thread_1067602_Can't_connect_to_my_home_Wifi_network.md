---
title: "Can't connect to my home Wifi network"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by d3uterius on 2009-02-12
Hi, i'm a true newbie with the linux system and i have this problem with the wifi network. I have the Hardy Heron on a Sony Vaio, and i can't connect to my wifi network. I have secured the network with a password, and the weird thing is that the laptop wouldn't connect, asking me from time to time the password again and again, and the icon from the upper panel is showing "waiting for the network key...". And yes, I have the correct password...:). The weird thing is that from windows the connection is running, and also from my iPhone. Need some advice please. Thanks.

---

### Post by prshah on 2009-02-12
> **d3uterius said:**
> 
i can't connect to my wifi network. 

from windows the connection is running, and also from my iPhone. 

You are probably not able to get an ip address, if the wireless password is correct. If you can post the following information it will be helpful for troubleshooting:

a) What security are you using? WeP, WPA, WPA2 etc? (Skip if you don't know)
b) Can you post the following from Windows? Click Start-Run and give the following commands```
cmd
ipconfig/all
``` and post back the output.

---

### Post by d3uterius on 2009-02-13
I'm using WPA security, anyways, i solved the problem by running the upgrade from 8.04 to 8.10. I mean, the problem has been solved by itself :D I really don't know what was wrong, anyways, something i did in the last 2 month...I tried to configure a Huawei hsdpa-3g modem and probably something i did affected the wifi normal functionality. But you were right, it wasn't able to get any ip adress or information. Everything was 0.0.0.0.0. Thank you for your help! :)

---

