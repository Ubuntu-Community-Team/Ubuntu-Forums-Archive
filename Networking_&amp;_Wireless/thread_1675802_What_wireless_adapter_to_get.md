---
title: "What wireless adapter to get"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by graabein on 2011-01-26
Hi, I have tried a couple of wireless adapters (USB dongles) but none of them work all that good on Ubuntu. I keep loosing connexion when on Ubuntu while on Windows (dual boot) there never seems to be any problems, so signal strength is probably not the issue. 

I bet it's a drivers problem so what I want to know is which adapters work really really good/great/fantastic on Ubuntu? 

Currently I'm using a D-Link GWL-G122 dongle 802.11bg. From Wicd Network manager I can choose between the following drivers:

[LIST]
[*]wext
[*]nl80211
[*]ralink_legacy
[/LIST]

The first option, wext, was chosen when I installed Wicd (running side by side with GNOME Network manager).

Should I perhaps try another? Any suggestions are welcome.

---

### Post by graabein on 2011-01-28
Nothing? Noone?

---

### Post by MrRichard on 2011-01-28
While I don't know one to suggest, I can tell you to avoid the D-Link WUA-2340. It never worked for me. Currently I'm using a seemingly no-name wireless card that I got with my PC. It has no logo or serial number on it :confused:

---

### Post by Boondoklife on 2011-01-28
[http://boondoklife.blogspot.com/2010/11/wireless-usb-adapter-ubuntu-friendly.html](http://boondoklife.blogspot.com/2010/11/wireless-usb-adapter-ubuntu-friendly.html)

---

### Post by bkratz on 2011-01-28
Also, you might check out this page

[http://wize.com/wireless-adapters/t117480-ubuntu](http://wize.com/wireless-adapters/t117480-ubuntu)

---

### Post by nickbishop on 2011-01-28
I have same problem!:confused:

---

### Post by MrRichard on 2011-01-28
Ah, here we go: cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html

I'm going to buy the Asus N13 first thing tomorrow morning :)

---

### Post by thenickrulz on 2011-01-29
ive got the asus n13 and it is working great.:guitar:

---

### Post by walt.smith1960 on 2011-01-30
I have a TrendNet TEW424UB ver.3.1.  It is recognized natively by every Ubuntu distro since 9.04 at least.  This is a G speed adapter.  Less smooth but working well are a Netgear WNA1100 (Atheros 9k chipset) and TrendNet TEW-649UB. I got the WNA1100 working with a .deb package from sourceforge.  The TrendNet uses a RealTek 8192SU chipset that requires a firmware file added in order to work.  These adapters are N 150Mb./sec. and are both recognized natively by the alpha release of 11.04.  I hope this helps.

---

### Post by OGpmpdog on 2011-01-30
Hi,

I use this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833130061](http://www.newegg.com/Product/Product.aspx?Item=N82E16833130061)

For Natty, wireless worked as soon as I plugged into USB port.

For Lucid, I had to go into terminal and type:

1) sudo gedit /etc/modprobe.d/blacklist.conf
2) in the gedit editor, skip to about the 3rd line, remove "number sign" quotes and enter: **blacklist rt 2800usb**

this took about 45 seconds - and I was good to go.

I never installed maverick, so I dont know...

Hope this helps.

---

### Post by graabein on 2011-01-30
Thanks for all the suggestions. I crosschecked the adapters at my local store against some internet source for Linux compatibility but it seems it's not a 100% fool proof, the one I got. Will read up on the links :D

I think I've got this one: 

> **D-Link DWA-140**
The D-Link RangeBooster NUSB Adapter (DWA-140) is a 802.11n compliant wireless client for your Linux desktop or notebook PC. I've tested this one with Fedora and Debian Linux. Like all other adapter it supports WPA and WPA2 security features. (Driver Link for RT2870)
Or maybe this is the previous one I tried but I think then the problem was weak signal because of the distance to the router...

---

### Post by walt.smith1960 on 2011-01-30
If you have the DWA-140, here's a thread that you may or may not be aware of.  The last post is an easy fix if it works for you.

[http://ubuntuforums.org/showthread.php?t=1633775](http://ubuntuforums.org/showthread.php?t=1633775)

---

### Post by Crim_Ferret on 2011-01-31
I also got a [COLOR=Lime]WNA1100 [/COLOR]working with the debian package after beating my head against the wall trying to make sense of conflicting instructions for getting it working. The installed command has to be run when one updates the kernel, but that's pretty minor. It does support WPA which is a requirement where I'm living. Be sure to check the support for that if it matters to you. I needed this fast for Windows and had to choose from what was available at Walmart at the time so I mostly lucked out that it works at all under Linux.

---

### Post by graabein on 2011-03-08
> **walt.smith1960 said:**
> If you have the DWA-140, here's a thread that you may or may not be aware of.  The last post is an easy fix if it works for you.

[http://ubuntuforums.org/showthread.php?t=1633775](http://ubuntuforums.org/showthread.php?t=1633775)

A late reply but hey... I've got the DWA-140 and it works okay, it's just that the signal keeps dropping out on Ubuntu 10.04, but not when I'm on Vista (dual boot).

---

### Post by Yellow Pasque on 2011-03-08
Netgear WNA1100 is what I use. Works without fuss on Maverick or later, or you can easily compile the linux-wireless module for older kernels/distros.

---

