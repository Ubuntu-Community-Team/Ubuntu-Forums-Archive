---
title: "Extremal Card Recommendation"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by heroquestelf on 2013-02-22
I have an Acer laptop that I've recently installed Ubuntu on. I'm an absolute novice, and I cannot get the wireless card to work despite doing all kinds of research on the internet and trying multiple solutions.

Long story short, I was told that the simplest thing to do would be to purchase an external USB network card that *does* play well with Ubuntu. 

I was wondering if anyone had any recommendations.

---

### Post by ersatzsplatt on 2013-02-22
buy new hardware when you already have something that should work?  that sounds like a terrible idea to me.
find out what you have and post it.
maybe you already know, but
'lspci | less'
will show you a list of all your pci bus connected hardware.  You should be able to look through that and see some kind of 802.11 something or another.
That can get you the chip vendor and device model information and add it to this post.
... your "all kinds of research on the internet", etc. is kind of vague, so I'm not sure how much more specific help will really be help to you at this point.

I'm not aware of an 802.11 vendor that does not have linux support (though I do know of at least one vendor that takes a couple steps to get it off the ground)

best of luck!

---

### Post by heroquestelf on 2013-02-28
I'm really sorry it took me so long to reply. I've been busy. Okay.. so what I have is an ACER 3613WLCi, but I'm having trouble finding the manufacturer of the wireless card. All it says is 802.11 b/g wireless lan. I found the name 'Broadcom" associated with some of the software, but I am not confident in this being the manufacturer of the hardware. What I see is a designation that says "bxmwl5a". I downloaded the associated drivers from the Acer website, and I found the "bcmwl5a.inf" file and tried to install it. When I did, the error I got was "Module could not be loaded. The Error was: FATAL: Module ndiswrapper not found. Is the ndiswrapper module installed?" The answer to this question is, "yes, the ndiswrapper module *IS* installed." Or rather, I've installed ndiswrapper, which is all that *I* know how to do.

Here is what I get when I type in the lspci -vvnn command: 
   06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02) 

     Subsystem: AMBIT Microsystem Corp. Aspire 3022WLMi, 5024WLMi, 5020 [1468:0311] 
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx- 
     Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
     Latency: 32 
     Interrupt: pin A routed to IRQ 10 
     Region 0: Memory at b0100000 (32-bit, non-prefetchable)  
     Kernel modules: ssb

Okay, update. I've been working on this thing all day. 

I wound up having to install the ndiswrapper -dkms package. Once I did that the indicator light on my laptop that shows my wireless card is working actually started blinking. However, despite my excited outburst, I still can't get online with it, as it will not recognize a wireless network. 

I'm sitting right next to the router, and I even pulled my tablet computer out to double check and make sure the router *WAS* sending out a signal.

[size=6]holy hoppin' moses on a pogo stick!! You can mark this thread "solved"

woooooooooo---hooooooooo!!!!!!

---

