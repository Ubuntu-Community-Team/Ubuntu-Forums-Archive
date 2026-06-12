---
title: "Pinnacle Studio 9 AV/DV card configuration"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by dwf_starband on 2007-06-18
How do i set up my Pinnacle Studio 9 AV/DV card?  It worked in windows so my machine is capible.
lspci shows,


~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
02:01.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Unknown device 0015
02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)

but tv time gives the error,

no such file or directory
cannot open capture device /dev/video0

any help with this would be greatly appreciated,

dennis

---

### Post by dwf_starband on 2007-06-19
anyone?

---

### Post by skirkpatrick on 2007-06-19
I believe I have the same card and found that there are no drivers for it.  I ended up buying a Hauppage PVR150 (not that I've actually used it yet).

---

### Post by dwf_starband on 2007-06-20
I have been using Ubuntu for about 6 months now and think that it is an amazing product.  I tell everyone about it.  It is my understanding that it is one of the most user friendly linux distributions avaliable and it has worked great for me.  I dont understand why the answer to a question like this is "get different hardware"  I thought the whole point of linux was that the possibilities were endless and that it can run on anything.  I understand that development is time consuming and for a project without $ comming in it cant really be anyones main focus.  It still seems to me that when a certain peice of hardware doesnt have a driver yet, that with a community this large, someone should be able to handle it.

I obviously have no skills in this department, and rely on those who know more than me for things like this,

so I expect nothing, and hope for everything

thanks for a great os

dennis

---

### Post by skirkpatrick on 2007-06-20
The problem comes down to the availability of information.  When you see drivers for hardware, either the manufacturer made their own driver (NVidia) or they made the necessary information available for the community to create the driver or somebody in the community has painstakingly spent huge amounts of time trying to figure out how the hardware worked and wrote a driver.  Most Linux drivers fall into the second category.  The third category usually only occurs either because of an extremely dedicated user of that hardware who has lots of spare time on their hands and electronic equipment to figure out how the hardware works or because the device is very simple.

I imagine the Pinnacle card is either difficult to figure out or not that widely used.  When I used Windows, I thought it was a great card for video capture and I really liked the software that came with it.  To be honest, telling a new Linux user that he may have to buy new hardware isn't any different than a new Apple user not being able to use all of his old PC hardware.

---

### Post by Deoden on 2007-08-31
> **dwf_starband said:**
> How do i set up my Pinnacle Studio 9 AV/DV card?  It worked in windows so my machine is capible.
lspci shows,


~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
02:01.1 FireWire (IEEE 1394): Pinnacle Systems Inc. Unknown device 0015
02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)

but tv time gives the error,

no such file or directory
cannot open capture device /dev/video0

any help with this would be greatly appreciated,

dennis


Hi dwf_starband

I have the same problem, but i have version 10. You resolve the problem????? Can you tell me anythink about it??

Thanks in advance.

PD: Sorry for my bad English.

---

### Post by dwf_starband on 2007-09-17
No, I never found anything out.  I ended up buying an actual tv tuner card w/ remote.  It should be here this week.

sorry for the bad news.

dennis

---

