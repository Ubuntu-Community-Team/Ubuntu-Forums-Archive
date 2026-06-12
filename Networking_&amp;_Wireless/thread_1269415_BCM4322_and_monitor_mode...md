---
title: "BCM4322 and monitor mode.."
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by vpnm_87 on 2009-09-18
I recently installed Jaunty in Dell Studio 1535..My internal wifi card works fine and i am able to browse well...

My lspci showed this:

```
 0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
```

I tried to put it in "monitor mode" but it showed this:
```

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
```

My connection information in Network manager applet shows my card uses "wl" driver...

Has anyone succeeded in puttin this card to monitor mode??

---

### Post by Ayuthia on 2009-09-18
The wl driver does not work in monitor mode.  Unfortunately, there no options that I know about that will provide this mode for your card.

---

### Post by vpnm_87 on 2009-09-18
Thnks for ur reply ayuthia..

I too spent a lot of time googling around and jus now decided to buy another external device to monitor my personal wireless connection..

"Broadcom always sucks"

Does b43 driver support "monitor mode" for this card??

(or)

if i hav to purchase a device to monitor how much does it cost and wat manufacturers are providing drivers n firmware to support monitorin??

can anyone provide some suggestion??

---

### Post by jml on 2009-09-18
It's my understanding that the Broadcom card you have simply does not support monitor mode in Linux.  I do not know if it supports that mode in Windows.  Drivers for the Broadcom card are difficult to come by since the manufacturer chooses to keep their drivers and the technical specifications for their cards proprietary.

If you have an old PCMCIA slot in your computer, you might try to look for a Cisco Aironet wireless card.  The old 802.11b gold card supports monitor mode in Linux, and their slightly newer Aironet 802.11a/b/g cards do as well.  Others may support monitor mode as well, but I do not have any experience with it.

What application are you planning to monitor your network with?  You might want to go to that application's web site and see if they list the wireless chip sets that their application supports.  Then you search for a card with that chip set and you should have better chance of success.  Good luck.

Joe

---

### Post by Ayuthia on 2009-09-18
> **vpnm_87 said:**
> 
Does b43 driver support "monitor mode" for this card??

It does not at this time.  The developers just finished getting the 14e4:4315 cards working and now they are working on the LP-PHY portion if I recall correctly.  After that, they will be starting on the N cards.  It might be a while for it, but I was quite impressed how quickly they got the 4315 card up and running.

---

