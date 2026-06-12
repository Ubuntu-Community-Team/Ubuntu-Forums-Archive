---
title: "ASRock MB onboard sound and lan fail."
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by thynk on 2007-04-17
I spent a few hours searching the forums for the answer and have gotten no joy.  I have a K8NF6G-VSTA motherboard system, the onboard video works just fine (need to install the Nvidia drivers for thepci-e  Geforce 6500 to work)

Here are some quick specs. 
chipset NVIDIA® GeForce 6100 / nForce 405
audio 7.1 CH Windows® Vista™ Basic Level HD Audio (ALC861VD/ALC883 Audio Codec)
lan Realtek PHY RTL8201CL 
link to MB [http://www.asrock.com/mb/overview.asp?Model=K8NF6G-VSTA&s=754AMD](http://www.asrock.com/mb/overview.asp?Model=K8NF6G-VSTA&s=754AMD)

Well, so far here is what I've done... 

o Install from Live CD Edgy 6.10 32bit 
o Download updates (drink coffee while updating)
o Install Nvidia driver with the Envy Script (**bows before the author** that script rocks)
o Compile from source the ALSA drivers (latest stable, 13 IIRC) and break the system
  - on boot it returns a /sbin/modprobe abnormal exit and won't mount / as RW only RO so none of the uninstall or reinstall fixes I found would work. 
*drink a few cups of coffee and smoke half a pack while I look for a solution*
o Give up  
o Reinstall Edgy 6.10 32bit
o Download updates
Post this posting

lspci stuffs... 
```
stu@lust:~$ lspci 
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:07.0 Bridge: nVidia Corporation Unknown device 03ef (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:09.0 PCI bridge: nVidia Corporation Unknown device 03e8 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d1 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0160 (rev a1)

```

The expanded lspci stuffs - I'd filter this to what I think is important but I'm not able to make this work so maybe giving more than is needed is the best idea :-)

```

stu@lust:~$ sudo lspci -nv
Password:
00:00.0 0500: 10de:03ea (rev a1)
        Subsystem: 1849:03ea
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [dc] HyperTransport: MSI Mapping

00:01.0 0601: 10de:03e0 (rev a2)
        Subsystem: 1849:03e0
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 0c05: 10de:03eb (rev a2)
        Subsystem: 1849:03eb
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at dc00 [size=64]
        I/O ports at 5000 [size=64]
        I/O ports at 6000 [size=64]
        Capabilities: [44] Power Management version 2

00:01.2 0500: 10de:03f5 (rev a2)
        Subsystem: 1849:03eb
        Flags: 66MHz, fast devsel

00:02.0 0c03: 10de:03f1 (rev a2) (prog-if 10)
        Subsystem: 1849:03f1
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at dddff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.1 0c03: 10de:03f2 (rev a2) (prog-if 20)
        Subsystem: 1849:03f2
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        Memory at dddfec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:04.0 0604: 10de:03f3 (rev a1) (prog-if 01)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: dde00000-ddefffff
        Capabilities: [b8] #0d [0000]
        Capabilities: [8c] HyperTransport: MSI Mapping

00:05.0 0403: 10de:03f0 (rev a2)
        Subsystem: 1849:0862
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at dddf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:06.0 0101: 10de:03ec (rev a2) (prog-if 8a)
        Subsystem: 1849:03ec
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at ffa0 [size=16]
        Capabilities: [44] Power Management version 2

00:07.0 0680: 10de:03ef (rev a2)
        Subsystem: 1849:03ef
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at dddfd000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d480 [size=8]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/3 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:08.0 0101: 10de:03f6 (rev a2) (prog-if 85)
        Subsystem: 1849:03f6
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 209
        I/O ports at 0e00 [size=8]
        I/O ports at 0e20 [size=4]
        I/O ports at 0e40 [size=8]
        I/O ports at 0e60 [size=4]
        I/O ports at c880 [size=16]
        Memory at dddfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:09.0 0604: 10de:03e8 (rev a2)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: ddf00000-dfffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cff00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0b.0 0604: 10de:03e9 (rev a2)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0c.0 0604: 10de:03e9 (rev a2)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:0d.0 0300: 10de:03d1 (rev a2)
        Subsystem: 1849:03d1
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at db000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at dddc0000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

00:18.0 0600: 1022:1100
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 0600: 1022:1101
        Flags: fast devsel

00:18.2 0600: 1022:1102
        Flags: fast devsel

00:18.3 0600: 1022:1103
        Flags: fast devsel

01:08.0 0200: 10ec:8139 (rev 10)
        Subsystem: 10bd:0320
        Flags: bus master, medium devsel, latency 32, IRQ 233
        I/O ports at e800 [size=256]
        Memory at ddeffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

02:00.0 0300: 10de:0160 (rev a1)
        Flags: fast devsel, IRQ 10
        Memory at df000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
        Memory at de000000 (64-bit, non-prefetchable) [disabled] [size=16M]
        Expansion ROM at ddfe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0
```

Now, pci lan cards are in fact a dime a dozen which is why I had a spare floating around, so I'm not overly concerned about that, except the engineer in me wants to make it "go".  I can drop a "lesser sound card" in the box, but that's the last solution.  

I'll be happy to post any additional info on here.  I'm trying to get a LMCE box working, and right now it ONLY installs on the 32bit version of Edgy, so I'm stuck with this for now.  

TIA, 

Stu

---

### Post by josephus on 2007-04-17
was responding to someone else's post when i stumbled on yours as well. it seems that the geforce 6100 chipset is problematic for a number of people.  

Based on this guys experience I would try running the Feisty LiveCD and see if your hardware is detected.
[http://ubuntuforums.org/showthread.php?t=393537](http://ubuntuforums.org/showthread.php?t=393537)

---

### Post by thynk on 2007-04-17
Gosh I hate people that beg for help in the forum and then go on to fix it themselves...  *grin*

Following this guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

with 1.0.14rc3 instead of rc1
and using 

```
options snd-hda-intel model=3stack
```


as the option, I now have sound... not sure how stable it is however - the first reboot after putting in the flavor option caused me to not boot, rebooted again and it came up fine.  Then I had a hard lockup while trying to post this the first time.

Looks like the .21 kernel will also support this, so fiesty users should be in luck. 

Lesson learned.... READ AND RESEARCH BEFORE YOU BUY!!!!

*grins*

Stu

---

### Post by josephus on 2007-04-17
I think this patch will get your LAN back up:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346)

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

### Post by treaz on 2007-05-14
Could you please mention once again exactly what driver from the ubuntu drivers you have chosen? I am currently using 7.04 and have a Asrock K8NF6G motherboard with a 405 intergrated chipset (it's a 6000 series equivalent). 
All the output i get is attached. I must add that if I choose a wrong driver and click on test the image gets screwed up (grey screen???) and the computer freezes. What am I supposed to see if all is ok? Tips?

Thanks in advance,
Treaz

---

