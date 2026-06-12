---
title: "Network-Manager"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by Spiqly on 2013-02-03
Hi everyone, i need some help to install Network-Manager i just updated my Ubuntu 11.10 to 12.10 and the DSL conection won't work so i wanted to reinstal it (remove and install again) but after i removed it i can't install again. Can anyone help me? 
Sorry for bad english and sorry if i post in the wrong place.

---

### Post by Bucky Ball on 2013-02-03
*Thread moved to **Networking & Wireless**.*

Welcome to the forums.

network-manager-gnome

... is what I have installed. Consequently:

```
sudo apt-get install network-manager-gnome
```

---

### Post by kurt18947 on 2013-02-03
> **Bucky Ball said:**
> *Thread moved to **Networking & Wireless**.*

Welcome to the forums.

network-manager-gnome

... is what I have installed. Consequently:

```
sudo apt-get install network-manager-gnome
```

Will that work if O.P. does not currently have a network connection?  If Network Manager is gone,  wouldn't  the O.P. need to establish a network connection manually, or from a CD/USB?

---

### Post by Spiqly on 2013-02-03
yes, i tried this but that's my problem. I don't have internet connection on ubuntu so i can't install any package from internet but i can download files from windows ( i have installed ubuntu and xp in dual boot) but i don't know what package i need and how to install it (without gdebi...it's not included in ubuntu 12.10)

---

### Post by kurt18947 on 2013-02-03
I don't have a CD or DVD with me.  It is possible to install Network Manager from a CD or USB.  This may be of some help:

[https://help.ubuntu.com/10.04/add-applications/C/offline.html](https://help.ubuntu.com/10.04/add-applications/C/offline.html)

This is using 10.04 as an example but it may give you an idea about how to proceed.

Synaptic is no longer included by default but I think Software Center should work as well.  The trick is you have to add the CD as a software source.  Once you're done I think you'll want to disable CD as a software source or you'll get a message each time you update software that the CD cannot be found or words to that effect.  I'm sure there are other sources you can find via Google about installing Ubuntu software without an internet connection

---

### Post by steeldriver on 2013-02-03
alternatively it should be possible to bring up a temporary network interface without network-manager (i.e. using ifconfig) - fairly straightforward with a wired connection, a bit harder (but shouldn't be impossible) with wireless - then reinstall network-manager from the regular online repos

---

### Post by Bucky Ball on 2013-02-03
Yes, network manager will be on the install CD. You need to tick that as a software source in Software Sources, update and then it should appear to install in Software Centre or Synaptics.

---

