---
title: "No web video at all...please help!"
date: 2011-03-19
forum: Multimedia Software
---

### Post by avocadorange on 2011-03-19
I have no flash video at all. Can you help me get it back?

I've had performance issues in Chrome and Mozilla with flash streaming video for months and am trying anything to fix the problems.

Today I wound up with no video at all. You tube videos are just a plain grey box now. Daily show is just plain black boxes where the videos are supposed to appear.

How can I fix this issue?

I should add I did a lot of cache clearing tonight in an attempt to solve my original problem.

---

### Post by avocadorange on 2011-03-19
Just to add some info in case this helps anyone identify the problem:

The icons in the bookmark bar also no longer appear. I just see plain white icons now. See screenshot attached.

Please let me know if I can supply any other info.

---

### Post by varunendra on 2011-03-20
Make sure you are not in "Work Offline" mode (File menu in Firefox).

Then open Synaptic Package Manager, type flashplugin, and install flashplugin-nonfree while uninstalling all other flash plugins (having more than one flash plugin may cause troubles).

If the above plugin enables youtube videos again but still there are performance issues, then try disabling hardware acceleration (right click flash video window > settings > enable/disable hardware acceleration), or post in detail the type of problems you are having.

---

### Post by avocadorange on 2011-03-21
Varun, 


thanks for your tips and response! It did help restore some flash video performance. The immediate problem is solved! I do have some questions and further background info about the original problem however.

**1) **Before installing '[COLOR="Blue"]flashplugin-nonfree[/COLOR]' I had been trying '[COLOR="Green"]adobe-flashplugin[/COLOR]' and 'ubuntu-restricted-extras' per the recommendation of qjmoss:
[http://ubuntuforums.org/showthread.php?t=1165338](http://ubuntuforums.org/showthread.php?t=1165338)

**what is the difference** between [COLOR="Green"]adobe-flashplugin[/COLOR] and [COLOR="Blue"]flashplugin-nonfree[/COLOR]?

2) The flash video is better than before but the underlying problems persist. The Daily Show site is still completely unwatchable and YouTube has freequent shockwave flash crashes. The issues I am describing happen in both firefox and chrome. (See attached thumbnails.)

3) The original issue was slow loading and choppy playback or "hiccups" when watching flash video in both chrome and firefox. I posted a thread [ [http://ubuntuforums.org/showthread.php?t=1680062](http://ubuntuforums.org/showthread.php?t=1680062) ]and didn't receive any help so I am now posting some further info here in the hopes someone can help. 

I did a lot of digging and finally I found the following information:

my system is as follows: [COLOR="Purple"]
Ubuntu 10.04
Kernel Linux 2.6.32-30-generic
GNOME 2.30.2

memory 432.8 MiB
Processor: Intel (R) Celeron (R) 1.40GHz
Avail disk space: 126.8 GiB

video card is: VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62][/COLOR]

(If I can provide any other info let me know.)

I also looked up system requirements for Adobe Flash Player 10.2
and found the following for linux:

Intel Pentium 4 2.33GHz, AMD Athlon 64 2800+ or faster processor (or equivalent)
512MB of RAM
graphic memory: 128MB of graphics memory (but I have no idea how to figure what my computer's graphic memory capacity is)
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

My **_amateur conclusion_**: [COLOR="Green"]adobe flash plugin [/COLOR]maxes out my CPU and uses up a great portion of my memory when playing videos in browsers. The system monitor generally confirms this: Usually I'm using 75% of memory and approaching 100% of CPU. Now that I'm using the "[COLOR="Blue"]flashplugin-nonfree[/COLOR]" I get more or less the same results as with [COLOR="SeaGreen"]adobe flash plugin[/COLOR].

I wonder how this happened because when I first installed ubuntu 10.04 I had great flash video performance. I could open a dozen or so video sites in tabs and enjoy them w/no problems. The system requirements for adobe flash may have increased while I wasn't paying attention. (This is the first time I've ever paid attention--out of desperation.)

So the questions continue:
4) Given my system limitations, is there an older version of flash player or a non-adobe equivalent such as gnash I should try? 

5) Should I install an older version of Ubuntu?

6) Any other ideas? _**[COLOR="DarkRed"]Anyone?[/COLOR]**_

7) Most importantly thanks for reading through all this and thanks in advance for any replies!

---

### Post by avocadorange on 2011-03-21
> **varunendra said:**
> 

If the above plugin enables youtube videos again but still there are performance issues, then try disabling hardware acceleration (right click flash video window > settings > enable/disable hardware acceleration), or post in detail the type of problems you are having.

Sorry but just to add something I cannot adjust the settings when I right click on youtube videos. I can adjust "global settings" but not "settings".

---

### Post by varunendra on 2011-03-21
> **avocadorange said:**
> 
**what is the difference** between [COLOR=Green]adobe-flashplugin[/COLOR] and [COLOR=Blue]flashplugin-nonfree[/COLOR]?
See [here]("http://askubuntu.com/questions/15408/flashplugin-installer-vs-flashplugin-nonfree-vs-adobe-flashplugin") (the second answer on this page)

> **avocadorange said:**
> my system is as follows: [COLOR=Purple]
Ubuntu 10.04
Kernel Linux 2.6.32-30-generic
GNOME 2.30.2

memory 432.8 MiB
Processor: Intel (R) Celeron (R) 1.40GHz
Avail disk space: 126.8 GiB

video card is: VGA compatible controller [0300]: ATI Technologies Inc RC410 [Radeon Xpress 200M] [1002:5a62][/COLOR]
Looks like 512MB RAM with about 80MB shared as "Video Buffer Memory" (you can check/set it in your BIOS)

10.04 recommends 1GB memory, although 512MB would do just fine, but may get overloaded with memory hogs like adobe flash player. So yes, this maybe a cause, but not necessarily.

How much swap you are using (sudo fdisk -l)? 1.5 to 2 GB is recommended for you.

Also, is your graphics adapter using correct driver with no conflicts? (some proprietary ATI drivers are known to have conflict with default fglrx drivers; see [here]("http://ubuntuforums.org/showthread.php?t=1563484")). If unsure, post the output of:
```
lspci -v
```
(result would be a long list, so wrap it in 'CODE' tags (select pasted output, and click on # icon on editing panel))

> **avocadorange said:**
> My **_amateur conclusion_**: [COLOR=Green]adobe flash plugin [/COLOR]maxes out my CPU and uses up a great portion of my memory when playing videos in browsers. The system monitor generally confirms this: Usually I'm using 75% of memory and approaching 100% of CPU. Now that I'm using the "[COLOR=Blue]flashplugin-nonfree[/COLOR]" I get more or less the same results as with [COLOR=SeaGreen]adobe flash plugin[/COLOR].
IMHO, this should exactly the case. However, I am no more mature on this than you.:)


> **avocadorange said:**
> 
4) Given my system limitations, is there an older version of flash player or a non-adobe equivalent such as gnash I should try? 

5) Should I install an older version of Ubuntu?
4) I don't have any recommendation right now, but you may try others. If any non-adobe plugin works for you, change to it without a second thought! Adobe plugin has a long history of poor design (for linux modules) causing over-usage of system resources. Unfortunately, no other plugin I know of has any better compatibility than adobe's.

5) I think you should try Karmik. I used to use it on a similar hardware without troubles with flash videos. But that was 6-8 months ago, so can't say if it would be same with newer kernel + plugin. Besides, it was pentium processor [P4 2.2 GHz, 512 MB RAM, ATI RC400]

> **avocadorange said:**
> Sorry but just to add something I cannot adjust the settings when I right click on youtube videos. I can adjust "global settings" but not "settings".
Yes, I noticed it too. It is disabled in the new plugin for some reason I don't know of. Google search didn't provide any reliable solution.

---

### Post by avocadorange on 2011-03-27
Thanks for your helpful reply, Varun! I may try Karmic Koala sometime in the future.I may just need to get a new computer. This Toshiba Satellite A100 was originally purchased in 2006, so perhaps it is simply unable to keep up with the latest graphics demands.

Here are a couple of questions:

1) > How much swap you are using (sudo fdisk -l)? 1.5 to 2 GB is recommended for you.

I ran the command and I couldn't see where it mentions swap. This is what I got:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
15 heads, 63 sectors/track, 124032 cylinders
Units = cylinders of 945 * 512 = 483840 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc289c289

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       66577    31457601    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8f10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       20110   161529523+   c  W95 FAT32 (LBA)
/dev/sdb2           20110       38914   151041025    5  Extended
/dev/sdb5           20110       38752   149742592   83  Linux
/dev/sdb6           38752       38914     1297408   82  Linux swap / Solaris
```


> Also, is your graphics adapter using correct driver with no conflicts?

I ran the command you suggested and got the following:

```
lspci -v
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 8440 [size=8]
	I/O ports at 8430 [size=4]
	I/O ports at 8420 [size=8]
	I/O ports at 8410 [size=4]
	I/O ports at 8400 [size=16]
	Memory at c0004000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 20000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: 66MHz, medium devsel
	I/O ports at 8450 [size=16]
	Memory at c0004400 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8460 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=04, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0200000-c02fffff
	Prefetchable memory behind bridge: 1c000000-1fffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeonfb, radeon

02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, medium devsel, latency 168, IRQ 23
	Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
	Memory window 0: 1c000000-1ffff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Device ff10
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at a000 [size=256]
	Memory at c0201000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

```

I have no idea how to interpret any of the above. I do see a lot of "access denied". I have no idea if that's 'bad' or not. I should add, thanks in advance to you, Varun, or to anyone else who can help out.

---

