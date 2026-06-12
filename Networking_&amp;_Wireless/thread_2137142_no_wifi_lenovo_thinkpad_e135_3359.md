---
title: "no wifi lenovo thinkpad e135 3359"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by jonasellemand on 2013-04-19
Hi everyone. I'm new so I don't know a lot.

I just installed Ubuntu 12.10 64bit on my new Lenovo Thinkpad Edge E135 3359. 

The problem is that the wifi connections does not even show up (I have to connect directly via cable). 

I dont know what to do or how to approach it from here.

Jonas

---

### Post by praseodym on 2013-04-20
Hi,

please show the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by jonasellemand on 2013-04-20
Spent most of the day on forums trying to figure out what to do and I finally managed. Dunno if the solution is stable yet though.


I downloaded this [http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb](http://jas.gemnetworks.com/debian/pool/main/w/wireless-bcm43142/wireless-bcm43142-dkms_6.20.55.19-1_amd64.deb)

Then did:
sudo apt-get install linux-headers-generic build-essential dkms

Then did:
cd Desktop   <--or wherever you downloaded the deb
sudo dpkg -i wire*.deb
sudo modprobe wl

---

### Post by jonasellemand on 2013-04-20
Cant seem to mark the thread as solved though. I'm clicking Thread tools and all I get is"Show printable...", "Subscribe..." and "Email...".

---

### Post by produnis on 2013-05-23
thanks man,
this works for me, too!

However, I found out that at least in Ubuntu 12.04.2 LTS, the "additional driver"-app (via system settings) shows a wifi driver that comes from the repository and works like charme, too


.

---

### Post by axelsvag on 2013-07-08
> **produnis said:**
> thanks man,
this works for me, too!

However, I found out that at least in Ubuntu 12.04.2 LTS, the "additional driver"-app (via system settings) shows a wifi driver that comes from the repository and works like charme, too


.

I have the same Lenovo with bcm 4313 but on Ubuntu 13.04 and I used the additional driver, but for me it consumes all badwith for all other in the network, Do you not experience the same?? If it is good for you I will go back to 12.04 also)))))

---

