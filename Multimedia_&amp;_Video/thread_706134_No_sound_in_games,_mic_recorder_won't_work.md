---
title: "No sound in games, mic recorder won't work"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by MrsDoubtfire on 2008-02-24
Hello,

I'm new to linux and I'm running Gutsy on an IBM thinkpad T60.  In messing around trying to get the internal mic to work with sound recorder I seem to have done more damage than help.  I got to the point where I could hear the microphone's output through my speakers, so I know the mic is not broken.  Some change I've made seems to have eliminated the sound in games (supertux says that sound and music are disabled, other games simply have no sound anymore), but mp3s still play.

Can anybody help me get things back to normal?>

Even better, can anybody help me get to the point where I can record sounds?

Thanks!

---

### Post by MrsDoubtfire on 2008-02-25
I looked though the sound problems guide on this site and got some info.  Unfortunately I am still an absolute newbie and don't really know what to do with this information.

-------------------------------------
when I ran aplay -l :
-------------------------------------

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---------------------------------
when I ran lspci -v :
---------------------------------

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Lenovo Unknown device 2015
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: ee100000-ee1fffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at ee400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: ee000000-ee0fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00005fff
        Memory behind bridge: ec000000-edffffff
        Prefetchable memory behind bridge: 00000000e4000000-00000000e40fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
        I/O behind bridge: 00006000-00007fff
        Memory behind bridge: e8000000-e9ffffff
        Prefetchable memory behind bridge: 00000000e4100000-00000000e41fffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=13, sec-latency=0
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: ea000000-ebffffff
        Prefetchable memory behind bridge: 00000000e4200000-00000000e42fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ee404000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
        I/O behind bridge: 0000a000-0000dfff
        Memory behind bridge: e4300000-e7ffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e3ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Lenovo Thinkpad R60e model 0657
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1880 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Lenovo Thinkpad R60e model 0657
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 18c8 [size=8]
        I/O ports at 18ac [size=4]
        I/O ports at 18c0 [size=8]
        I/O ports at 18a8 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at ee404400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: medium devsel, IRQ 11
        I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA])
        Subsystem: Lenovo Unknown device 2006
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at ee100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at ee120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
        Subsystem: Lenovo ThinkPad T60
        Flags: fast devsel, IRQ 16
        Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 3000 [size=32]
        Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1010
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at edf00000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at e4300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
        Memory window 0: e0000000-e3fff000 (prefetchable)
        Memory window 1: 50000000-53fff000
        I/O window 0: 0000a000-0000a0ff
        I/O window 1: 0000a400-0000a4ff
        16-bit legacy interface ports at 0001



-------------------
I also tried the following:  (which changed nothing)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

and

sudo apt-get install gdm ubuntu-desktop
--------------------

summary:

the old problem:
-I could not record anything with sound recorder

new problems since i tinkered with Volume Control and Multimedia System Selector and maybe installing/ uninstalling things (newbie mistakes maybe?)
-there is no sound in games (music files still play)
-I can hear what the mic is picking up through the speakers whenever I start up (terribly annoying)
-I *still* can't record anything.

Sorry for the long long post.  Please help!~

Thanks!

---

### Post by MrsDoubtfire on 2008-02-25
OK, so I fixed the problem of hearing the mic playback when I did not want to.

By going into sound preferences and at the bottom of the screen where it allows you to select the device and tracks to control with the keyboard and changing it from microphone back to Master.

Still stumped on what else might have happened to eliminate sound in games.

EDIT:
internet streaming audio for sites like youtube doesn't work either.

---

