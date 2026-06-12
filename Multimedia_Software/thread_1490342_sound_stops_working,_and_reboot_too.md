---
title: "sound stops working, and reboot too"
date: 2010-05-22
forum: Multimedia Software
---

### Post by wasabishot on 2010-05-22
Hey guys,
I'm facing a quite frustrating issue with my ubuntu 10.04
i upgraded a week ago, on my HP Pavilion 9730us laptop.

what happens is that randomly my sound stops working, without making any change, for example, i watched a movie last night, everything fine, woke up and sound not working, restarted one time, still wasn't working, than tried to reboot again, but it kept bringing me to the login screen. so i forced shutdown with long holding power button, turned on the laptop and everything is working fine again.

this problem happens almost everyday.

last actions i took were :
1. installing RTL 8187 drivers for my new ALFA AWUS036H wifi adaptor.
2. using aircrack to hack a wep .
3. while doing the last 2 things, my internal wifi card has stopped working, so in order to make it work again, i did 
```
$ sudo apt-get remove  --purge linux-backports-modules-*
```

and then unsitalled/reinstalled brodacom STA drivers.

4. updated alsa drivers to 1.0.23 version.



any ideas of how to make everything stable without having to reboot all the time???
please help!!

thanks in advance!!!

---

