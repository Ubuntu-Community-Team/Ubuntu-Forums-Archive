---
title: "Linksys wusb54gc (1737:0077) no scan results"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by mach3 on 2009-11-22
Hi

I have just installed ubuntu 9.10 from scratch and plugged in the Linksys wusb54gc wireless stick.

I can see the device with ifconfig however it is not possible to see any results with the scan.

Anyone help will be appreciated. Stuck with windows 7 until then.

---

### Post by AFI420 on 2009-11-22
same here. This thing has been a pain. The closest I got was using ndiswrapper, but never got connected. I think it was because I didnt setup WPA supplicant correctly. But Ill try it again with security turned off and post results if they work

---

### Post by mach3 on 2009-11-22
> **AFI420 said:**
> same here. This thing has been a pain. The closest I got was using ndiswrapper, but never got connected. I think it was because I didnt setup WPA supplicant correctly. But Ill try it again with security turned off and post results if they work

Ok great thank you!

---

### Post by mach3 on 2009-11-22
Is this the approach?

1. Identify chipset vendor 

2. Download the relevant driver from ralink website

3. Recompile the ubuntu kernel (with make?)

4. Everything works and everyone is happy :o)

---

### Post by AFI420 on 2009-11-22
mmm some what, theres more configuring at the end of that. Ive read that we have to blacklist other drivers, copy files to other folders, add stuff to startup, play with dhcp, etc. im hoping ubuntu will patch this problem asap, i will use my wired connection until then (30ft wire running across the room)

i read somewhere that the drivers dont link to the device ID (1737:0077) a goof by ra

---

### Post by mach3 on 2009-11-22
> **AFI420 said:**
> mmm some what, theres more configuring at the end of that. Ive read that we have to blacklist other drivers, copy files to other folders, add stuff to startup, play with dhcp, etc. im hoping ubuntu will patch this problem asap, i will use my wired connection until then (30ft wire running across the room)

i read somewhere that the drivers dont link to the device ID (1737:0077) a goof by ra

Just happy with the windows 7 right now!

---

