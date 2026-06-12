---
title: "NForce3 250Gb or ATI Radeon Problem?Somebody help, PLEASE!"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by reibax on 2006-01-28
Hi everybody!

I'm trying to make my 3D acceleration work, and I've read through all the posts related to Radeons and NForces, but I haven't been able to find a solution to what happens to me.

I've alredy posted a similar post in another thread, but as I think my particular case could deviate from the topic I've decided to start a new one... I hope I can solve this. I am very patient, so I will definetly stay with my Kubuntu distro, as I like it very much, but it would be superb to have all of my hardware running correctly.

My system specs:
AMD Sempron64 3400+
ASUS K8NE-Deluxe nforce3 250gb
512MB of RAM
ATI Radeon 9700 Gold 128MB agp 8x
(and more)
Kubuntu Breezy 64 bit Edition


I think the problem I have is caused beacause of Linux not having the appropiate drivers for our Motherboard/Chipset, and I don't really know how I can fix that.  I've reached this conclusion beacause of these outputs:

```

$ dmesg | grep fglrx
[   29.083111] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   29.085371] [fglrx] Maximum main memory to use for locked dma buffers: 364 MBytes.
[   29.085844] [fglrx] module loaded - fglrx 8.21.7 [Jan 14 2006] on minor 0
[   53.955579] [fglrx:firegl_unlock] *ERROR* Process 7422 using kernel context 0

```

Note that the fglrx module has been loaded correctly.

```

~$ lsmod |grep agp
NOTHING COMES UP!!

```

No agpgart, no nothing :confused: 

```

~$ modprobe agpgart
FATAL: Module agpgart not found.

```

```

reibax@reibax:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)
0000:02:08.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev d1)
0000:02:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:02:0a.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:02:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
0000:02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

Host Bridge: NVidia corporation: unknown device??¿? Well, may be I'm wrong, but that seems to be the problem... the question is... :-k How can we get that fixed? PLEASE!! SOMEBODY HELP!!!

---

### Post by madmetal on 2006-01-28
got the same chipset and working great with MSI m/b and nVidia card.
so either the Asus m/b or the ati card have the problem.
look for drivers maybe( i don't know about Ati problems)

---

### Post by reibax on 2006-01-29
Thanks for your reply. I've tried every howto related to ATI and fglrx, and I've not been able to get it working.

I've also looked for NVidia drivers, but all I've been able to find is the Sound Driver, which I don't need because I've got an Audigy2 ZS and the motherboars sound system disabled, and the LAN driver, but the networking part of my motherboard is working ok.

If you know of a Driver for the chipset I would be more than willing to try it and see if it works correctly.

---

### Post by madmetal on 2006-01-29
i haven't looked for drivers,
ethernet audio (o/b) all working fine !
i wil give a try and tell..

---

### Post by reibax on 2006-01-29
Thank you very much for your time and effort. As a really desperate attempt, I've just downloaded Dapper Filght 3 Live CD, and all my o/b hardware was correctly detected, so what I have just done is take my Kubuntu to suicide and I've replaced all of my "breezy" words in /etc/apt/sources.list with "dapper", and using the package manager I'm trying to upgrade my system to Dapper beta, I'll tell you if this experiment has got a happy ending or a tragic one.

See you soon.

Regards:

Reibax.

---

### Post by reibax on 2006-01-29
Game Over!

My system isn't working any more... upgrade has failed before upgrading the aptitude system and now I can't resume it... I guess I will have to reinstall the hole system, and I think I'm going to give Dapper Beta a try, as I've found the LiveCD really interesting.

Now I've got three weeks of exams, but after I'm done with that I will try to get my system up and running, and I will post here if I can configure everything successfully. Thanks for reading!

Regards:

Reibax.

---

### Post by madmetal on 2006-01-29
good luck with exams! 
try to make ATi working good and its ok!
if the sound and network work fine there's no need to look for driver (in my oppinion)

---

### Post by madmetal on 2006-01-29
good luck with exams! :) 
try to make ATi working good and its ok!
if the sound and network work fine there's no need to look for driver (in my oppinion):-k

---

### Post by alanrr_sr on 2006-06-11
I can have my system working without any problem, but i am not able to enable 3d graphics. My computer is a Asus K8n-e too, but I have a ati 9550 xt hardware. I always get something like "unable to acquire agp" or something like that, even in dapper (32 or 64). 
But if I boot on windows, and reboot on linux, my 3d works perfectly.

Good lucky....

---

### Post by Slim Backwater on 2006-06-27
Not sure if you found a solution, but I'm having the same problem with Slackware 10.2  I think it's a hardware/ Linux/ Driver issue rather than a distro issue.  I have the same solution as alanrr_sr, which is to boot into windows and then reboot into linux, then 3D works.

*Edit: Well there you go.  Downgrade your BIOS to 1006.

[http://www.ubuntuforums.org/showpost.php?p=1185716&postcount=12]("http://www.ubuntuforums.org/showpost.php?p=1185716&postcount=12")

---

