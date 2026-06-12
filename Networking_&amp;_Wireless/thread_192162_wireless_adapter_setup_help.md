---
title: "wireless adapter setup help"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by mccarthy on 2006-06-08
I did a search but I wasn't really sure what to look for so...

I just set up a wireless network in my house with a linksys router.  My home PC, the one wired to the router, is on windows xp.  I have Ubuntu 6.06 on my other PC and I got a wireless adapter for it, but I don't know how to get my computer to recognise the PCI adapter.  When I go to network settings I only see my on-board lan eth0 and the one for the phone line (i forget what it's labelled).  I think I need to get my computer to recognise that I have put in a new PCI card (so somthing like eth1 shows up), and also probably install drivers for the card.  The CD that came with the adapter has 4 versions of drivers for Debian systems, and I don't know which one to use or how to put it on my system (there's a windows .exe file on the CD but I'm pretty sure that's useless to me).  The adapter is the EDIMAX EW-7128G PCI Wireless Card:
[http://www.newegg.com/Product/Product.asp?Item=N82E16833315041](http://www.newegg.com/Product/Product.asp?Item=N82E16833315041)

please tell me if you need more information, and thanks for the help!

---

### Post by mccarthy on 2006-06-09
Ok I rebooted and all of a sudden the card showed up, and it found my router.  However, it would not connect to the internet.  Then I rebooted again (after activating the ra0 thing in Networking), and the computer hangs during the boot process when it gets to the network initialization step (I forget exactly what the screen says, I'm at work right now).  It just sits there forever.  If I disconnect my adapter the computer boots normally, but plugging it back in causes the boot process to hang again.  Please help me!

---

### Post by mccarthy on 2006-06-09
Pressing ctrl+c gets me past the "configuring network interfaces" part and to the login screen, but logging in does not bring up the desktop, it just hangs at the brown gdm background.  I can not get on my computer when this wireless card is in a pci slot.  Please help!

EDIT
I think I juist need to install the correct driver, but I have NO IDEA how to do this.  If someone could indicate which driver is the right one and explain how to get it on my system I would be very very very very grateful.

---

### Post by bodycoach2 on 2006-07-12
I'm having the same trouble. Did the crtl+c, and stuck at brown screen after login.

---

