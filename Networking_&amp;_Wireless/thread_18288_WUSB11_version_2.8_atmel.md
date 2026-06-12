---
title: "WUSB11 version 2.8: atmel"
date: 2005-03-05
forum: Networking &amp; Wireless
---

### Post by otterit on 2005-03-05
I've been trying for 2 days to get a Linksys WUSB11 version 2.8 NIC to work with Ubuntu without success.  Based on a lot of research on the web, I learned the easiest way to setup the NIC would be to install ndiswrapper.

To date, using Synaptic I have installed the ndiswrapper and wireless-tools packages.  Unfortunately, when I load the run 'sudo ndiswrapper -i NETUSB.inf' with drivers provided on the CD and/or the drivers downloaded from Linksys I receive the following error:

> Installing netusb
> no dev USBNETXP28.Ndi NT.5.1

I then plugin the USB NIC and type ndiswrapper -l  and it says:

>Installed ndis drivers:
>netusb  hardware NOT present.

Does anyone have an easy to follow solution on how to use this USB NIC with Ubuntu?  I believe the WUSB11 v2.8 is using an Atmel chipset, but I'm not 100% sure.

Any help would be GREATLY appreciated!!

---

### Post by otterit on 2005-03-07
Zero replies...

I guess that is all I need to know.

 :(

---

### Post by KenLin on 2005-03-07
[QUOTE=otterit]Zero replies...

I guess that is all I need to know.

 :([/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11](http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11)

---

### Post by otterit on 2005-03-08
[QUOTE=KenLin][http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11](http://ubuntuforums.org/showthread.php?t=14030&highlight=wusb11)[/QUOTE]

I'll try it again.  It didn't work last time.  :(

---

### Post by kheldorin on 2005-03-13
nt

---

