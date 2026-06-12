---
title: "TL-WN823N Has anyone tried this WIFI usb adapter?"
date: 2013-01-13
forum: Networking &amp; Wireless
---

### Post by deckoff on 2013-01-13
Hello everyone.
I think about buying this one TL-WN823N for my Zbox Id41. 
I really like the small form factor and the up tp 300Mb speed.
This device seems to be quite new, it is not even in the database. 
Is anybody using the device, what about installation, etc?
I am on 12.04

---

### Post by kurt18947 on 2013-01-13
It looks like it could work.  Here's some hardware info:

[http://www.wikidevi.com/wiki/TP-LINK_TL-WN823N_v1](http://www.wikidevi.com/wiki/TP-LINK_TL-WN823N_v1)

RealTek offers a linux driver for that chipset if the 'built in' one doesn't work.  If the install is similar to the rtl8188CUs, it's pretty straight forward.  You could search the networking and wireless forum for rtl8192cu and see what users experience has been with that chipset.

---

### Post by deckoff on 2013-01-13
I have a no-name Realtek RTL8192CUS USB adapter and it is awful. 
I t takes years for the dongle to connect.
I dont know if the reason is that the device is no-name and is literally falling to pieces, or because of the chip itself?
OK, thanks for the help :)

---

### Post by ahallubuntu on 2013-01-13
> **deckoff said:**
> I have a no-name Realtek RTL8192CUS USB adapter and it is awful. 
I t takes years for the dongle to connect.
I dont know if the reason is that the device is no-name and is literally falling to pieces, or because of the chip itself?
OK, thanks for the help :)

Did you install Realtek's driver for it instead of using the crappy driver in the 12.04 and 12.10 kernels?

---

### Post by deckoff on 2013-01-13
Yeah, I installed the driver, I have even starred the askubuntu page about installing it. It is down to running a bash script and blacklisting a drive, I suppose this is what you mean?
As I said, I bought a really cheap dongle from e-bay, so than also might be the case.

---

### Post by ahallubuntu on 2013-01-13
I have a couple of these cheap RTL8192CU dongles and (after building the Realtek driver) they work quite well for what I use them for: connecting my media centers to the internet.  They are only 150Mbps  though.  I don't stream HD content from a NAS, I only watch stuff online, but I get solid connections.

---

### Post by kurt18947 on 2013-01-14
> **deckoff said:**
> Yeah, I installed the driver, I have even starred the askubuntu page about installing it. It is down to running a bash script and blacklisting a drive, I suppose this is what you mean?
As I said, I bought a really cheap dongle from e-bay, so than also might be the case.

What does your 'lsmod' command show?  I'm using a Edimax ew-7811Un.  It shows the module '8192cu'  I believe the 'built-in' module displays as 'rtl8192cu' which I blacklisted along with every other wifi related module except '8192cu'.

---

### Post by deckoff on 2013-01-14
I threw this adapter in the bucket this morning. It fell to pieces. I bought TL-WN821N v4.1 this morning, which is based the very same realtek chipset (not atheros anymore). It works pretty well with the driver from the Realtek site. I manged to watch HD 1080p video, located at my NAS without any hiccup. The Nas is connected to the router with a cable.
PS I just bought WN823N and will test it out, too. Should be working fine since it is based on the same chipset :)

---

### Post by flash63 on 2013-01-14
Hi, the system module rtl8192cu works unfortunately wrong. 

I have provided a corresponding installation package with the current bustle of Realtek for DKMS. The module is tested and works fine.

Link (german ubuntuusers):

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5210562](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5210562)

With Ubuntu 10.04 you maybe must use an older Pakage for rtl8192cu - Version 3.4.2-3727:

[http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#post-2844083](http://forum.ubuntuusers.de/topic/mein-wlan-stick-150n-von-sitecom-spinnt/#post-2844083)

---

### Post by scarabcoder on 2013-01-14
Well, what computer are you using? If you are using a Desktop, I would reccomend going [here]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4389486&CatId=2701")

---

### Post by deckoff on 2013-01-14
I use 8192cu, not rt8192cu. Kernel is 3.2.0.35, and ubuntu 12.04.
I should change my info, really, I have 3 PCs on 12.04, two on 11.10(cos not in use or always in use) and none on 10.04 :)

lsusb:

```
ID 0bda:8178 Realtek Semiconductor Corp
```

It is working OK now.
While we are on the subject, can I disable the built-in wireless, cos it is are just popping around in the menu and is slower.

---

