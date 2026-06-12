---
title: "no sound in karmic, soundcard not detected"
date: 2009-11-02
forum: Multimedia Software
---

### Post by djzoid on 2009-11-02
hi all, just upgraded to karmic on my eee 900 and regretting it! i know this threads been repeated but i have not seen anything that actually helps. i only have so much time to trawl through similar posts, got studies to do too! 

i have no sound whatsoever. i began to follow the instructions from [http://ubuntuforums.org/showthread.php?p=8218261](http://ubuntuforums.org/showthread.php?p=8218261) but to no avail. 

```
alexi@raziel:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

alexi@raziel:~$ aplay -l
aplay: device_list:223: no soundcards found.
```this isnt completely neccesary but i dont know how to try to identify just my sound card:

```
alexi@raziel:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d9
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d9
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d9
    Flags: bus master, fast devsel, latency 0
    Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 8337
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: fbf00000-fbffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
    Memory behind bridge: f8000000-fbefffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d8
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at e400 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d8
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at e480 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d8
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at e800 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d8
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at e880 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d8
    Flags: bus master, medium devsel, latency 0
    Kernel modules: intel-rng

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device 82d8
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 82d8
    Flags: medium devsel
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Device 1a3b:1026
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath_pci, ath5k

03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device 8233
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
    Expansion ROM at fbfa0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: atl2
    Kernel modules: atl2
```

im dying to listen to some tunes so any help would be appreciated.

---

### Post by p110011 on 2009-11-02
Hey, I had no sound after upgrade to 9.10. Seems my Kernel was not, so I used Synaptic package manager to remove the old one and install the correct one. linux-headers-2.6.31-14

To check your Kernel:
```
uname -a
```

---

### Post by djzoid on 2009-11-02
im not sure but think i have the right kernel:

```
alexi@raziel:~$ uname -a
Linux raziel 2.6.30.5-ep0 #10 SMP PREEMPT Thu Aug 27 19:45:06 CEST 2009 i686 GNU/Linux
```

i looked in synaptic and had 2 packages with that name in the title installed.

i could try to install the others with linux-headers-2.6.31-14 in the title but dont know what they are or if i should?

---

### Post by p110011 on 2009-11-02
If you do a quick search in the package manager entering Linux-Image you will see the one that you have installed and boot to 2.6.30 along with Linux-Image 2.6.31 which is the one I am using for Karmic. Also when you boot up (depending on if you dual boot or not) you can see the kernel and most people leave two on their systems in-case one causes problems and you can fall back to the last known good one. I think if you just install 2.6.31 it may just move to the top of the list.

---

### Post by djzoid on 2009-11-03
things seem fine now, but i did just install pretty much all the headers including the linux-rt stuff cos i use lmms. lmms doesnt seem to go for long still without the cpu bar being eaten up like mad which isnt normal, bad latency.

 the sound prefs in karmic are a bit bizarre. nice touch with the app specific volume controls tho. 

i did have the wrong kernel, just didnt pay proper attention to what i was reading p110011 lol:???:

thanks for the help!!

edit: erm,  4th line down, 64bit non-prefetchable? not sure that's right... i seem to have installed the pae kernel on a 32 bit system, is this wrong?

 i cant get my head around the physical address extension thing, i like linux but im in way over my head most of the time!

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device 8337
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


$ uname -r
2.6.31-14-generic-pae

---

### Post by p110011 on 2009-11-03
Glad you got it going.:D

---

### Post by arturic on 2009-11-25
[SOLVED] well, sort of...

I have a Gateway CX2735m tabletPC, the audio device is SigmaTel STAC9250 (ICH7 family). I did a fresh ubuntu 9.10 install so my problem wasn't an old kernel.
I had no sound and the sound prefereces showed no audio hardware and in the output tab I only saw a dummy device.

I did the shell stuff shown here: [http://ubuntuforums.org/showpost.php?p=8218261&postcount=60]("http://ubuntuforums.org/showpost.php?p=8218261&postcount=60")
and here: [http://ubuntuforums.org/showpost.php?p=8254699&postcount=65]("http://ubuntuforums.org/showpost.php?p=8254699&postcount=65")

```

alsamixer
alplay -l
lspci -v
grep 'audio' /etc/group
cat /proc/asound/modules

```

and everything looked OK, the sound device was properly detected there, but still I had no audio hardware on the System > Preferences > Sound (by the way volume and mute keys worked OK) and if I tryed to play a video or audio file I didn't get any error, I simply got no sound.

I also tryed this with no results:
```

sudo apt-get install linux-backports-modules-alsa-karmic-generic

```

So I followed the link about ALSA (see the later link above postcount=65) I found that my soundcard was coupled with the software modem in my machine, then I remembered I activated a propietary driver for the software modem at intall time...

**The Solution: I turned off the propietary software modem driver at System > Administration > Hardware Drivers**, and it started working even without a reboot !!! and the audio hardware was properly detected at sound preferences.

Now the only problem is that I have the software modem driver disabled, but anyway I haven't use a dial up connection since 2002 I think. Still It'd be nice to have it usable, Any advice here?

Well, I hope this can be usefull to someone, cheers! ;)

---

### Post by washakie on 2010-01-24
Just a second on the method. Worked perfectly for me as well...

In fact, all I did was follow arturic's bold print:
> 
**The Solution: I turned off the propietary software modem driver at System > Administration > Hardware Drivers,** and it started working even without a reboot !!! and the audio hardware was properly detected at sound preferences.

_Metadata:_
$uname -a
Linux jfb-field 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
$lspci -v 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30b1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4780000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

