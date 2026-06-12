---
title: "Wifi wont show up"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by tomstud12 on 2013-05-10
hello i have ubuntu 12.04 and i want to connect to internet by wifi but it wont show up and when i press the wifi switch the light wont turn on but when i had windows xp it worked so can you please help me

---

### Post by tomstud12 on 2013-05-10
hello i have ubuntu 12.04 and i want to connect to internet by wifi but  it wont show up and when i press the wifi switch the light wont turn on  but when i had windows xp it worked so can you please help me

---

### Post by tomstud12 on 2013-05-10
hello i have ubuntu 12.04 and i want to connect to internet by wifi but  it wont show up and when i press the wifi switch the light wont turn on  but when i had windows xp it worked so can you please help me

---

### Post by praseodym on 2013-05-10
Please open a terminal with CTRL+ALT+T and show the outputs of the commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
lsmod
rfkill list
```

---

### Post by grahammechanical on 2013-05-10
Ubuntu is not crafted to work with that machine as Windows was. Linux distributions try to be a one size fits all product and so are not machine specific. You have to do things differently. Have you set up a wireless connection to your router?

[https://help.ubuntu.com/12.04/ubuntu-help/net.html](https://help.ubuntu.com/12.04/ubuntu-help/net.html)

When you installed Ubuntu did you have a wired connection or a wireless connection? Have you clicked the Network Manager icon in the top panel. Do you see a list of wireless access points in range? Is your wireless access point listed? Is networking enabled? Is WiFi enabled? 

Regards.

---

### Post by QIII on 2013-05-11
*Threads merged and moved to **Networking and Wireless.***

Please do not start duplicate threads in multiple areas of the forums.

---

