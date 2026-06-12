---
title: "Unable to connect to Wi-Fi using Ubuntu 13.04 64-bit"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by Col936 on 2013-06-16
This is a rather odd problem. I have a Gateway LT2704u netbook. Earlier today my previous installation of ubuntu freaked out. It had some random process consuming half my CPU, it had networking disabled and locked, and was freezing randomly. I restarted the computer several times, and faced the exact same problem, every single time. I gave up on it and decided to reinstall the OS. I reinstalled it with the same version and bit as my old one: 13.04 64-bit. While installing the OS it worked without a hitch. After rebooting to apply the install, I noticed that I wasn't connected to Wi-Fi. I opened up the menu, and no wi-fi networks were appearing. Ethernet works fine. I ran ifconfig in the terminal, and it only showed my Ethernet connection, eth0, and something called lo. It was a local loopback something or other, but that doesn't matter. I disconnected the Ethernet cable, and it still didn't show my wireless.

This is a huge problem for me as I rely greatly on the internet for my day-to-day computer usage. Any help at all would be great :)

---

### Post by Hadaka on 2013-06-16
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
```
thanks

---

