---
title: "Hoary doesn't recognize Belkin P5D6001 802.11b PCI card"
date: 2006-03-06
forum: Networking &amp; Wireless
---

### Post by lkvee on 2006-03-06
There's a reuse center in NYC that opened up this weekend.  I've been tasked with setting up a PC with WiFi access.   Since none of the suitable PC boxes have a Windows XP Product Key, I decided to install Linux.   

The box of choice features an Athlon 750 Mhz Socket A CPU on an Asus A7V motherboard with 256 MB of (tested) memory.   I actually originally tried to use Warty at first, but I later discovered that the ndiswrapper package wasn't on the CD.   

Hoary didn't recognize my Belkin PCI 802.11b WiFi card.   I followed the ndiswrapper instructions for this card, even using the special parameters to use the RealTek drivers.   When I executed the "sudo ndiswrapper -l" command, I did get the "net8180 drivers present", but I didn't get any messages about hardware.

I discovered the adm8211 drivers, but when I tried to execute the "make install" command, I got an error message about a missing separator.

I'm afraid I'm not talented enough to dig deep inside and tweak anything accordingly.   Anything else I can do to get this WiFi setup up and running?

I also thought about using a 3Com 10/100 Ethernet card, and hooking that up to a Belkin 802.11b router.   Don't really care how WiFi's setup, as long as it is.   

Thanks for reading.  I'm looking forward to reading the replies.

---

### Post by lkvee on 2006-03-06
I can't seem to find the functions that let me edit the Subject line.   Sorry.

---

