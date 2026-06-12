---
title: "How to connect to wifi on 10.04 LTS installed on Dell"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by nengard on 2010-06-10
I just installed 10.04 LTS on my husband's Dell laptop but don't know how to get my wifi to work.  I did some searching here in the forums and found a bunch of posts, but all are from 2008 or earlier meaning that they are probably not for my version of Ubuntu - feel free to tell me that the steps are the same.

Anyway, I did a 'lspci' in Terminal and the important lines that appeared are:

03.00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base0TX (rev 02)
0c.00.0 Network Controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

So my system does recognized the wireless card, I just don't know how to get Ubuntu to find available networks. I tried adding in our network as a 'hidden' network - which it isn't and that didn't work, so I'm up for any suggestions in how to get the computer to connect to the wifi network?

Thanks!!

---

### Post by nengard on 2010-06-10
Just an update - I did read here: [https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html](https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html) but I don't know where 'Network Manager' is - I looked everywhere ... is this referring to the wifi icon on the top right of the screen?

---

### Post by gsgleason on 2010-06-10
Yes, that is the network manager applet.  For me, when I click on it, I get a list of all the available wireless networks.

Try this from a terminal:
```
sudo iwconfig
```
See if your wireless interface is shown.  Mine is wlan0.
If so, then do this:
```
sudo iwlist wlan0 scan
```

---

### Post by nengard on 2010-06-10
Found a solution !! [http://ubuntuforums.org/showthread.php?t=1390979&page=3](http://ubuntuforums.org/showthread.php?t=1390979&page=3)

---

