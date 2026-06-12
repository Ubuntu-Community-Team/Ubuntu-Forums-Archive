---
title: "Problem setting up Pixima MX700 printer with samba"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by Ianprime0509 on 2009-02-07
Okay, I'm trying to use a Canon Pixima MX700 printer via Samba to my dad's computer. I was able to get it working by a wired connection, but it's my dad's printer so I have to do wireless.

So I went into the printer setup, selected Samba Printer, and I clicked browse and found the printer after setting it to share with Windows XP on my dad's computer. Then, I clicked Verify and it said that "The print share is not accessible". I tried using the IP address instead of the /MSHOME/FAMILYROOM, but that didn't work. I also unchecked "Enable Bidirectional support" and tried again, but that didn't help either. Is there something vital that I'm missing? Thanks.

---

### Post by FishRCynic on 2009-02-08
inane and maybe useless questions:
ubuntu version is ?
the above is i386 (32bit) or amd64 (64bit)?



network setup up is?

xp computer directly wired to printer via usb cable
xp computer wired to router (with wireless access point)
linux machine wireless to router (with wireless access point)

or 

xp computer wired to router (with wireless access point) via ethernet cable
printer wired to router (with wireless access point) via ethernet cable
linux machine wireless to router (with wireless access point)

or advise


ps did you do as the networking manual asks:


  Note
To set up the machine that is not yet connected to a LAN, connect the machine and the computer with a
USB cable.
Even if the machine has been set up to be used with the USB connection, follow the setup procedure
described in this manual to connect the machine to a LAN for the first time.

from canon support site:
mx700_nsg_u4_v1.pdf

---

