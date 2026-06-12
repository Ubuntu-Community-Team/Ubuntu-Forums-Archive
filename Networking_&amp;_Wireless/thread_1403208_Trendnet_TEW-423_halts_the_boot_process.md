---
title: "Trendnet TEW-423 halts the boot process"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by mark bower on 2010-02-10
I purchased the TEW-423/C1.1R based on posts which indicated it works with Ubuntu (or at least linux) out of the box.  I wanted a card that was supported with native drivers - no messing with ndiswrapper and such.  The Trendnet TEW-423 is posted as working out of the box with the Realtek chip RTL8185.  My unit has the chip (RT8185).  The posting is at    [http://linux-wless.passys.nl/query_part.php?brandname=TRENDware](http://linux-wless.passys.nl/query_part.php?brandname=TRENDware)

With the card inserted, Ubu 9.04 and 9.10 freeze at boot time.  9.10 freezes when the logo appears, 9.04 freezes at the arrow which comes after the logo.  Remove the card and full boot is enabled.  Obviously this card is not working out of the box.  Any suggestions or does someone have a wireless PCI card that truely works out of the box.

mark

---

### Post by chili555 on 2010-02-10
This is a known bug and I have, so far, found no solution. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368679](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/368679)

Post #4 seems encouraging, albeit perhaps anecdotal. If you'd like to attempt to compile the Realtek driver, I'd be happy to assist. 

As well, you could go shopping for a better card.

---

### Post by mark bower on 2010-02-10
@chili555

For now, I would prefer to simply obtain a PCI NIC card that absolutely works out of the box, althoh I appreciate your offer to help with the compile effort.  My Belkin F5D7050s are out of the box devices, however, I drive thru 3 walls and some 40 feet, thru wire mesh in one case, and would like to get more than one bar.  And please realize, I did my homework when purchasing the TEW card and according to the link I provided in 1st post the RTL8185 is listed as working out of the box.  I looked at the link you provided, and indeed complications all over the place!

So, please tell me if you can which currently sold PCI NIC card(s) in fact do work out of the box(drivers supplied by kernel, 2.6.28-11 or later).  I already have Hawking increased gain antenna's.

mark

---

### Post by mark bower on 2010-02-11
bumped for chili555 or other response.

what PCI wireless card, with removable antenna, works out of the box with 9.10?  that is, fully handled by native drivers, no ndiswrapper requirement.

mark

---

### Post by mark bower on 2010-02-11
bumped again for reply and/or chili555 attention.  what pci wireless card works out of the box with 9.10?

mark

---

### Post by mark bower on 2010-02-14
what pci wireless card(s) works out of the box with 9.10, no ndiswrapper?

mark

---

### Post by chili555 on 2010-02-14
I have no direct experience with any PCI wireless cards. All I can suggest you do is scan this: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Try to match up what is supported with what's available in your area.

---

