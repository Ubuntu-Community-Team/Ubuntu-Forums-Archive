---
title: "how to install wlan ?"
date: 2012-03-14
forum: Networking &amp; Wireless
---

### Post by yelena1 on 2012-03-14
hello,

i'm beginner in computer i just need it to email and get information in internet.  my old computer died and i get a laptop from a friend but without windows. 

i have installed ubuntu newest version. i dont understand how to use wlan.
the wlan is intel centrino advanced-n 6200 agn.

[LEFT]i find this [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads) and download the file [iwlwifi-6000-ucode-9.221.4.1.tgz]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000-ucode-9.221.4.1.tgz")

inside there is  description how to install but i dont understand this
[/LEFT]

[URL="http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6000-ucode-9.221.4.1.tgz"]

Installation of the firmware is simply:

% cp iwlwifi-6000-4.ucode /lib/firmware

You can now load the driver[/URL]


where i have to paste this code ?

---

### Post by chili555 on 2012-03-14
I am quite certain that if you installed the latest Ubuntu version, the driver and the firmware are already installed. Let's check. Please open a terminal and enter these commands. Post the result here in your reply:```
lspci -nn | grep 0280
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

