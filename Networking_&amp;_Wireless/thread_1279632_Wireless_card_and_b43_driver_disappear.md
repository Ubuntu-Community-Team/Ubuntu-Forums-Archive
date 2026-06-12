---
title: "Wireless card and b43 driver disappear"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-10-01
Hi all. I had a nightmare with and never got my Broadcom wireless card going in 7.04. When I eventually loaded 8.04 - probably over a year ago - it picked up my card, alerted me there were restricted drivers available and I just followed my nose; set up in five minutes and haven't had a problem since. All happened 'automagically!'

Until now.

History: Update yesterday, my wife did it so not sure what the updates were. 

My laptop does something I've never bothered fixing. If you get to the login screen and walk away it eventually goes into hibernate I guess: screen goes black and makes some reaction when you touch the mouse but then dead.

Normally you just reboot the machine and all is well. Today, I rebooted the machine only to find my wireless card and the b43 driver have completely disappeared. Red light on card and B43 driver missing from Hardware Drivers. I was getting this message:

siocgifflags error: no such device

I plugged in a cable and typing from that connection. Any help appreciated. I have reinstalled b43-fwcutter but not sure how to go about the rest. Any way of getting the system to pick up the card and offer me the restricted drivers a'la the original scenario?

Maybe a bizarre combination of booting after the updates and then going into the odd hibernation/re-boot pattern. One can only imagine, great timing though; end of uni year and haven't got a lot of time to fix or I would spend more time figuring it out before posting! :)

* PS: wlan0 - which is what the wireless card was - has disappeared from everywhere.

---

### Post by Bucky Ball on 2009-10-01
Really weird. The card has totally vanished, drivers and all. 

```
~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

I'm starting to wonder if the card has simply died. Any thoughts??? :-k

---

### Post by Bucky Ball on 2009-10-01
I don't like where this is going. This page suggests this is a known problem and getting HP's attention on it is difficult; my laptop show exactly the symptoms described:

[http://www.asifism.com/hp-quickplay-windows-vista/trouble-with-hp-laptops-wireless-broadcom-cards/](http://www.asifism.com/hp-quickplay-windows-vista/trouble-with-hp-laptops-wireless-broadcom-cards/)

uh-oh. Did a security update kill it? Looks like the netbook might be coming sooner than later ...

---

### Post by Ayuthia on 2009-10-01
Here is the link from [HP]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=uk&docname=c01087194").  I had this problem with my dv6338se laptop and had to send it in.  Mine was within the two years of purchase so it was covered and repaired within a week's time.

When this happened to me, I originally had the wireless card become visible and then disappear.  I reinstalled Vista and it would work for a little while, but then it finally just quit. 

HP ended up replacing the motherboard on it.  From what I understand, they did not regulate the fans correctly so at some point, the motherboard quits finding the wireless card.  That was the reason why they request people to switch over to that BIOS version in the Limited Warranty page.

---

### Post by Bucky Ball on 2009-10-01
Yep, thanks for that. What I was afraid off. Bad news is no sign of it in Windows either. Damn. I've had mine for about a year and a half. Will it be covered? I'll drop them an email.

I updated the BIOS when my screen started acting oddly and the fan is running at a constant hum as it is supposed to rather than in short bursts as it was. Card/Motherboard still crapped out. I think I might get a USB wireless dongle as suggested on another page. I can't really wait for HP to fix it right now even if they will.

---

### Post by Ayuthia on 2009-10-01
> **Bucky Ball said:**
> Yep, thanks for that. What I was afraid off. Bad news is no sign of it in Windows either. Damn. I've had mine for about a year and a half. Will it be covered? I'll drop them an email.

I updated the BIOS when my screen started acting oddly and the fan is running at a constant hum as it is supposed to rather than in short bursts as it was. Card/Motherboard still crapped out. I think I might get a USB wireless dongle as suggested on another page. I can't really wait for HP to fix it right now even if they will.

Mine was about that old and it was covered.  Of course, I am in the US so that might make a difference.  I did end up removing Linux off of the laptop before sending it back out of fear of them not fixing it and spending several days working with them to cover it (also known as I was too chicken).

Good luck!

---

### Post by Bucky Ball on 2009-10-05
Well, I emailed HP suggesting I might re-install the OS to see if that gets the card up. They were very helpful(!) and said 'yea, do that and get back to us.' Can't imagine what they might say if it doesn't work (and from what I've heard it might but doesn't last long) but all hope is not lost.

They certainly haven't mentioned they've seen this problem with any of their machines before.

---

### Post by Bucky Ball on 2009-11-18
An old thread I know but this is where it ended up. The motherboard died. My laptop, being the HP dv6305us is covered for the recall in America:

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&product=3370281&docname=c01087277#c01087277_identify](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&product=3370281&docname=c01087277#c01087277_identify)

And even though there is the same recall in the Asia-Pacific region, the dv63** is not there; only goes as far as the dv62**:

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01296338&lc=en&dlc=en&cc=au&lang=en&product=3370281](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01296338&lc=en&dlc=en&cc=au&lang=en&product=3370281)

So if I was in the states it would be covered because it is a known issue but in Australia I'm screwed. That can't be right. Problem is, my warranty officially ended in July 2008 and this problem started in October 2009 (they are offering the repair for up to 24 months after the START of the warranty period). 

Where do people think I should go with this? I registered the machine when I bought it and there was about six months left then. It was in December 2007. I've had it for 23 months and it is dead. Not really happy for AU$1300.

I might post a separate thread and see what people think. ;-(

---

