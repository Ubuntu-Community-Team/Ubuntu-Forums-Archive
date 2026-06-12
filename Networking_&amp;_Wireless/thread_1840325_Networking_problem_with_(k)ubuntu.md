---
title: "Networking problem with (k)ubuntu"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by mobruu on 2011-09-07
Hi!

Just installed Ubuntu 11.04 and installed kubuntu.

Have a dualboot with win 7 starter and ubuntu 11.04.

Problem is the wireless networking within kubuntu.

Works perfectly fine with Gnome and "standard" ubuntu.
Works fine with Win 7.

Using WEP at home and I cannot connect at all. kubuntu locates the network, and I enter the password. After 2-3 minutes the "password dialogbox" pops back up.

Here's the funny part. Using WPA/WPA2 personal at work, I have no problems getting a connection with kubuntu.


Any clues?

Thanks for any replies :-)

---

### Post by wildmanne39 on 2011-09-07
Hi welcome to the forum! I am about to leave town until later this afternoon but please run these commands in a terminal by hitting ctrl+alt+t and post the results here:
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
dmesg | grep -i -e warn -e error
```
```
lsmod
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by SeijiSensei on 2011-09-07
If it were me, I switch my router to WPA2 Personal.  Is there some special reason why you need to run WEP?  I presume you know that it's [not very secure]("http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Flaws").

Kubuntu has never had problems connecting to my WPA2 Personal network except when the kernel driver for my RT2500 device was borked (which seems to happen with every other release of Ubuntu).

---

### Post by mobruu on 2011-09-07
Changed to WPA2 personal, and it works like a charm :-)


Thanks for the tip and help :-)


-M

---

### Post by wildmanne39 on 2011-09-07
Hi, glad you got it working I suspected it was possibly a wep issue but I wanted to wait until I saw the out put from the commands before saying so. 

Would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

