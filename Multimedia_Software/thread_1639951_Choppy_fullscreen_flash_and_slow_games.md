---
title: "Choppy fullscreen flash and slow games"
date: 2010-12-07
forum: Multimedia Software
---

### Post by purplehayes2400 on 2010-12-07
Hi,

I recently installed Ubuntu on my laptop (Acer Aspire 3500). I played around with two different versions (both had some issues). I believe the version of Ubuntu i am running is 10.4. I am extremely pleased to have removed window from my computer.

I am having two problems:

1.) Full screen flash video is choppy 

2.) Games (either run in wine or run straight from desktop (eg "tux racer")) have choppy, slow graphics and the mouse cursor is really slow.

I do not have much experience at all with this new OS and desperately want to resolve these issues. I have tried on my own for almost two weeks now with no success. Please advise me and assume I am an idiot when you do so.

Cheers and thanks,

tony

---

### Post by TBABill on 2010-12-07
It is important that you know what you installed (10.04 or 10.10) and if you are using 32 bit or 64 bit. Your version of flash plugin should match which you are using. But, more importantly, you probably need the correct video driver in order to get decent performance out of the machine, especially for games. With the open source drivers you are limited to 2D performance but the proprietary driver, if available, will give you 3D performance and much improved desktop response.
 
Can you provide the output of ```
lspci
``` in a terminal so we can see what video card you have?

---

### Post by purplehayes2400 on 2010-12-07
Thank you for your response. 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


I am 99% sure my ubuntu is 10.4 - How do I check this? I appreciate your help very much.

---

### Post by TBABill on 2010-12-07
To check the version I just usually do ```
uname -a
``` but you need to know what the return means. If it is 2.6.32-whatever, then you have 10.04. If it is 2.6.35-whatever, then it is 10.10. That is the kernel version and each uses a different kernel. It will also say x86_64 or i386 (I think), the first being 64 bit and the other 32 bit.
 
Your video card is an SIS. I am unsure what drivers that brand uses since I have no experience with them. Perhaps searching the forums for SIS would return some usable results to continue troubleshooting or maybe someone else will respond to be able to help more with it.

---

### Post by purplehayes2400 on 2010-12-07
2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

So 10.4 it is -- i do not see how to tell 32 or 64

I will search for SIS driver information.

Once again thank you and if anyone else can steer me in the right direction please do!!

peace,

tony

---

### Post by Yellow Pasque on 2010-12-07
SiS Linux drivers suck.
Flash on Linux sucks (unless you have an nvidia card and you run their proprietary driver).
Conclusion: you're screwed.

---

### Post by purplehayes2400 on 2010-12-07
lol - i was getting that feeling - I have uninstalled and reinstalled all of the adobe flash options and none work in full screen - I will just live with it - truth is even with the video limitations I feel great without microsoft on my computer - guess that's the breaks - fortunatelt I am in Korea and if I get the gaming urge their are plenty of pc rooms around.

Thanks for confirming my fears.

tony

---

### Post by TBABill on 2010-12-07
And just to add a bit of insight, the i686 at the end of the output of uname -a means you are running 32 bit Ubuntu.

---

### Post by #Vader# on 2011-01-21
Hello,
I just fixed my choppy full screen by right clicking on an active flash video, select "settings" "display tab" and unchecked 

"enable hardware acceleration".   Hope this helps

I have an Acer travelmate 4010, brought back to life by Ub10.10

---

