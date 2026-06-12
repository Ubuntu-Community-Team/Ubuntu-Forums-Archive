---
title: "Sound detected; none heard on Ubuntu 9.04"
date: 2009-05-20
forum: Multimedia Software
---

### Post by dragonsbane375 on 2009-05-20
I am using a computer that is custom built.  I have a motherboard with onboard Audio and Video.  Audio is the Intel ICH4 series of the AC'97 Audio Controller.  The video is this in my Hardware Profile.htm:  82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device.

I have no sound at all.  Not even after login or before logout.  I have checked the PulseAudio Device Chooser's Volume Meter (Playback) to see if it register's sound.  It always does.  Yet, I hear nothing all the same.  Is there anything I can do.  I have been through all the guides I could find.  Either they have what I need up to a certain point, they are incomplete and not fully comprehensive, or they offer me no solution at all.
I am using Ubuntu 9.04 Jaunty Jackalope x86 Architecture.  Any help would be appreciated.

EDIT:  I think the main reason this is such a problem for me is all the guides are for laptops.  I have a desktop.  I am unsure if the instructions are still the same and that leads me to hesitate.

EDIT:  EDIT:  I guess I could keep adding info until I solve my problem...

lspci -v returns this:

```
dan@dragon-lorekeeper:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 5770
    Flags: bus master, fast devsel, latency 0
    Memory at e8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 5778
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at ee000000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 5770
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 5770
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 5770
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Micro-Star International Co., Ltd. Device 5770
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ee080000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: ec000000-edffffff
    Prefetchable memory behind bridge: 40000000-400fffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. Device 5770
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at f000 [size=16]
    Memory at 40100000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 5770
    Flags: medium devsel, IRQ 17
    I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 5771
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at e000 [size=256]
    I/O ports at e400 [size=64]
    Memory at ee081000 (32-bit, non-prefetchable) [size=512]
    Memory at ee082000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Micro-Star International Co., Ltd. Device 577c
    Flags: bus master, medium devsel, latency 32, IRQ 23
    I/O ports at c000 [size=256]
    Memory at ed000000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at 40000000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

```

Then when I run:

```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh
```

I get this webpage:

[http://www.alsa-project.org/db/?f=2d958d73e83065336290fb532e2edaabd5d98a1f](http://www.alsa-project.org/db/?f=2d958d73e83065336290fb532e2edaabd5d98a1f)

Which says a bunch of stuff that this guide made me try and sort through:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I hate ADHD.  As I cannot sort through all of this information in one sitting and I want to get my sound working, I cannot believe that I have done all that I have thus far.

Also:
```
grep 'audio' /etc/group
```

Returns this:
```
dan@dragon-lorekeeper:~$ grep 'audio' /etc/group
audio:x:29:pulse,dan
```

Still need help...

---

### Post by dragonsbane375 on 2009-05-21
[FONT=Century Gothic][SIZE=3][COLOR=Blue]](*,)BUMP[/COLOR][/SIZE][/FONT][FONT=Century Gothic][COLOR=Blue]](*,)

[COLOR=Black][SIZE=2]

[SIZE=2]I would appreciate a fairly quick response from someone who can in anyway help me...[/SIZE]I am really wishing I could get some sleep tonight...Want to at least pretend I feel better tomorrow.  Forgive me if I seem pushy or grouchy...Felt slightly ill all day, that's gotten worse, and I really don't want to hit the hay until I feel that I have made some progress instead of the running-around-without-any-results-what-so-ever-like-a-chicken-without-its-head sort of feeling I have right now...Please try and get to my issue as soon as possible.  To those who feel I may have bumped early, it is a new day here...And I cannot stay awake another moment as of the sendding of this post...sorry...g'night..

EDIT:  I just put in a new card.  That fixed my problem (After disabling onboard of course).  I would to take this time to comment that the lack of response is almost cruel in nature...and from now on will refrain from using these forums.  gl with your endeavors.
[/SIZE][/COLOR][/COLOR][/FONT]

---

