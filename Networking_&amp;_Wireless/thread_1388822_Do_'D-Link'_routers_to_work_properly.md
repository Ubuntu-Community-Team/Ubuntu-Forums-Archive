---
title: "Do 'D-Link' routers to work properly?"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Papa-san on 2010-01-23
When I first started using Ubuntu, I had a D-Link router that I could not make work, and the general consensus of the Ubuntu users I was talking with was that the best bet was to just get a Linksys router. My son and I swapped routers then. I have his Linksys, he has the D-Link.
Evidently, WOW wrote a patch that has killed his ability to play through the D-Link, and he needs his other one back. 
Since there were such problems back then, and I found my solution, I quit following the router issues. I was just wondering if this set of issues was resolved and I can now use the D-Link, or should I get my own Linksys?
He is going to send me the particulars about the D-Link, and I will post those once I get them...

Thanks!
John

---

### Post by ajgreeny on 2010-01-23
Are you really asking about routers or do you mean wireless adapters?  It is most unusual for a router to make any difference at all to the ability of a computer to connect to the web, but some adapters are known to be troublesome with linux distros.

---

### Post by CharlesA on 2010-01-23
How would a WOW update break a router? Seriously.

I've used both dlink, belkin and linksys routers with Linux with no problems.

It could be the network card in the machine, if you are connecting wirelessly.

---

### Post by Papa-san on 2010-01-23
Well, I'm not entirely sure... That's why I have to ask...
I am trying to connect wirelessly. The first laptop I had was a Dell latitude C-610, and I couldn't get it to work wirelessly with the D-Link.
(For whatever reason.)  I swapped it for the Linksys, and it just worked. I switched to a Latitude D-610, and the transition was nearly seamless. 

I believe his problem is his cable connection, but there is no way to convince him otherwise once he has an idea in his head. (Two neighbors are also experiencing problems with their cable connections today, so that makes 4 of us.) He's convinced the patch screwed something up, and I won't get any peace until he has this router back. 

I guess I could probably make the switch and start fighting with whatever it might be to get my wireless back. (It's just frustrating, because the Windows laptops here will likely connect right up without any issues.)

here is my current system info:```
john@john-latitude:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
john@john-latitude:~$ 
```

---

### Post by Papa-san on 2010-01-23
Here's the info on the router:
the router is a dlink di-624+ revision C

OK... So is a "network controller" and a "wireless adapter" the same thing?

---

### Post by bkratz on 2010-01-23
This line is the wireless adapter

Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver

---

