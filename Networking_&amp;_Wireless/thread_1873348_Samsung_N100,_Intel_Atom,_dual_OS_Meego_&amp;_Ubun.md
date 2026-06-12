---
title: "Samsung N100, Intel Atom, dual OS Meego &amp; Ubuntu. How to configure Ubuntu?"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Tanvile on 2011-11-01
Hi,

I've installed Ubuntu alongside Meego (and also repartitioned the memory a bit, but no data was lost).
 
But Ubuntu did not configure network: I can't connect neither to wired, nor to wifi. 

Also, when running under failsafe boot, it displays a message that, e.g., graphics card, network and sth, don't remember correctly, are not configured and I have to configure them manually.

I've searched for configuration apps in GUI, but failed. Also, info manual in the terminal did not give any clue to the silly me.

Help? What to enter the command line to at least configure the network?

---

### Post by Rhizoid on 2011-11-01
I'd start with... ```
lspci | grep -i ethernet; lspci | grep -i wlan
``` which will tell you what devices have been recognised.

---

### Post by Tanvile on 2011-11-01
> **Rhizoid said:**
> I'd start with... ```
lspci | grep -i ethernet; lspci | grep -i wlan
``` which will tell you what devices have been recognised.

ok, so in meego it prints like this:

```
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

```

And the same for Ubuntu. Though for wlan both return nothing, a new line is printed.


**Any hints on what to do further on**? :) Or, at least, any references to some good and comprehensible material on terminal to read? :)

---

### Post by Tanvile on 2011-11-01
Ok, so after consulting
[here]("http://ubuntuforums.org/showthread.php?t=1873158"), [here]("http://ubuntuforums.org/showthread.php?t=1873518") and [here]("http://wiki.debian.org/iwlagn"), I finally found out that the thing has all of the drivers needed, at least for wifi.
Also, ```
nm-tool
``` showed just what I needed - the wired connection was there, just disabled. 
Question is, why and how was it disabled so that it does not autoreconnect after rebooting?

UPDATE: funny thing I found in [Ubuntu wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek").
It says that the driver
```
r8169
```, which happens to be the driver of my Realtek wired network card, is incorrect and is thus unreliable with this card.

Though wired connection did work previously... Up until my teacher "fixed" the network settings when I asked to help me to configure the wireless xD

That's it for now, researching further on.

---

### Post by Tanvile on 2011-11-01
So, in the end, all I needed was to manually change /etc/networking/interfaces to contain
```
auto eth0
iface eth0 inet dhcp
```Also, it could be static adresses from ```
ifconfig
#and
/etc/resolv.conf
```Thus, I restarted the networking:
```
/etc/init.d/networking restart
```It didn't work at first, then I reloaded Meego, 
read a bunch of references on networking, found nothing, 
logged in to Ubuntu again and - voila! - it's alive :)

It must have needed overall system reload.

I'll try to configure also wireless tonight.

Thus, this thread is SOLVED

References:
[Old and too-easy]("http://ubuntuforums.org/showthread.php?t=28242"), but helped the most :)

---

### Post by maha2139092 on 2011-12-19
I am using dual os XP + Ubuntu...
in xp wifi working fine...
in Ubuntu wifi not at all detecting..
only lan is working..
pls help me... i have followed you suggested steps but..
no improvement...


Thankyou

---

### Post by maha2139092 on 2012-01-02
this thread is not solved pls any body help how will i enable wifi in samsung n100 laptop in ubuntu 9.10

---

### Post by maha2139092 on 2012-01-02
Not working with SAMSUNG N100 netbook WIFI Pls help Me...

> **Tanvile said:**
> So, in the end, all I needed was to manually change /etc/networking/interfaces to contain
```
auto eth0
iface eth0 inet dhcp
```Also, it could be static adresses from ```
ifconfig
#and
/etc/resolv.conf
```Thus, I restarted the networking:
```
/etc/init.d/networking restart
```It didn't work at first, then I reloaded Meego, 
read a bunch of references on networking, found nothing, 
logged in to Ubuntu again and - voila! - it's alive :)

It must have needed overall system reload.

I'll try to configure also wireless tonight.

Thus, this thread is SOLVED

References:
[Old and too-easy]("http://ubuntuforums.org/showthread.php?t=28242"), but helped the most :)

---

### Post by Rhizoid on 2012-01-02
9.10 is end of life - why not just upgrade to 10.04 and see if that fixes the problem?  I have a friend with the N100 and WiFi has never caused him a problem, but then he's always been on 10.04 or later.

---

### Post by maha2139092 on 2012-01-21
> **Rhizoid said:**
> 9.10 is end of life - why not just upgrade to 10.04 and see if that fixes the problem?  I have a friend with the N100 and WiFi has never caused him a problem, but then he's always been on 10.04 or later.

I have tried with Ubuntu 10.04 also its not working... i am not interested to update 10.10 or 11.04
i hate the unity panel please suggest me to solve issue..

The thing is Wlan device not detecting..

i have tried via windows wifi driver to ndswrapper no response

thankyou

---

### Post by fakrulalam on 2012-09-07
Try upgrading the kernel version.

# uname -r
# apt-cache search linux-image
# apt-get install linux-image-3.0.0-24-generic

Reboot and hope it will detect your Wi-Fi. Still trying to solve the graphics issue. Resolution is not supported higher than 800*600

---

