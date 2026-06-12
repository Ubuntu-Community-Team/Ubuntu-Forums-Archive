---
title: "ifconfig wlan0 up - no such device"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by templeof on 2013-04-03
Hello I got a strange problem, after I made update on my ubuntu 12.04 1 update finished with some error, after I rebooted my computer, I can not start wlan0

my **ifconfig wlan0 up** results in 

"**ERROR while getting interface flags: no such device**".. had someone the same problem? or can someone advice how to proceed or fix it?
(I started the computer with liveDVD knoppix and it works fine, wifi works perfect)

thx in advance

---

### Post by chili555 on 2013-04-03
No such device wlan0 usually means the hardware and driver haven't joined and created a cute little child that they named wlan0. The driver may not be loading for some reason or it is trying to load and an error causes the process to abort. Let's troubleshoot. Please open a terminal and run and post:```
lspci -nn | grep 0280

```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

