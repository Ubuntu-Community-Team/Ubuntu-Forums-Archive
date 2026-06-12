---
title: "Amarok kills digital audio, sound only then plays from headphones"
date: 2008-08-03
forum: Multimedia Software
---

### Post by chrono13 on 2008-08-03
Symptoms of the problem:

After using Amarok (even after closing it and confirming it is closed) I attempt to play an AVI in Totem and it has no audio, except through the headphones.

I then attempt the same with mplayer (which throws an error that there is no sound). I was unable to capture this error as it has happened twice and I can not easily reproduce the issue with mplayer, as most of the time instead of throwing the error, it plays through the headphones.

VLC plays correctly through the speakers (digital), but only most of the time. That is probably the strangest part of this bug.

Restarting my computer after using Amarok fixes the issue.

To reproduce quickly: even though I do not use Totem at the same time as Amarok, this appears to be the quickest way to reproduce the bug (although just using Amarok with nothing else open can cause it as well).

1. Open Amarok and begin playing music.
2. Open a video with audio in Totem. This will cause all sound (both Totem and Amarok) to be through the headphones only by disabling the digital audio out.
3. Close Amarok and Totem. Digital audio is now disabled, and the only way to fix is to restart the computer (disabling and re-enabling it via the Volume Control switches does not correct the issue).
My volume control reads: "Volume Control: HDA NVidia (Alsa mixer)"

I use the digital out on my system. The analog out is unaffected by this problem. I have a very nice set of speakers, and I do not want to have to switch back to the analog.

Also note that when starting Totem, there is a faint click or short crackle through the speakers, as if the digital is turned off *each* time it is launched (necessary file in use by another app?)


Any ideas?


details (while afflicted with the bug):

lsof /dev/dsp (nothing returned)

lsof /dev/snd/*
```

COMMAND     PID    USER   FD   TYPE DEVICE SIZE  NODE NAME
mixer_app 12789 devnull   20u   CHR  116,0      12163 /dev/snd/controlC0

```


uname -a
```

Linux navix 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

```


aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


lspci -v
```

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fc000000-fe9fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fea00000-feafffff
	Capabilities: <access denied>

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 5000 [size=64]
	I/O ports at 6000 [size=64]
	Capabilities: <access denied>

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fbffec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f462:7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=8]
	I/O ports at b080 [size=4]
	I/O ports at b000 [size=16]
	Memory at fbffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at ac00 [size=8]
	I/O ports at a880 [size=4]
	I/O ports at a800 [size=8]
	I/O ports at a480 [size=4]
	I/O ports at a400 [size=16]
	Memory at fbffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fbff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fbff7000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at a080 [size=8]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: eVga.com. Corp. Unknown device c615
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
	Capabilities: <access denied>

02:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 320a
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at feaffc00 (64-bit, non-prefetchable) [size=128]
	Memory at feafc000 (64-bit, non-prefetchable) [size=8K]
	I/O ports at dc00 [size=128]
	Capabilities: <access denied>

04:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 350d
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: <access denied>

```


ps -e
```

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:24 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:00 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:07 events/0
   16 ?        00:00:04 events/1
   17 ?        00:00:01 events/2
   18 ?        00:00:02 events/3
   19 ?        00:00:00 khelper
   54 ?        00:00:01 kblockd/0
   55 ?        00:00:00 kblockd/1
   56 ?        00:00:01 kblockd/2
   57 ?        00:00:01 kblockd/3
   60 ?        00:00:00 kacpid
   61 ?        00:00:00 kacpi_notify
  171 ?        00:00:00 kseriod
  230 ?        00:00:01 kswapd0
  273 ?        00:00:00 aio/0
  274 ?        00:00:00 aio/1
  275 ?        00:00:00 aio/2
  276 ?        00:00:00 aio/3
 1713 ?        00:00:00 khpsbpkt
 1736 ?        00:00:00 ksuspend_usbd
 1741 ?        00:00:00 khubd
 1742 ?        00:01:46 ata/0
 1747 ?        00:00:02 ata/1
 1748 ?        00:00:00 ata/2
 1749 ?        00:00:00 ata/3
 1750 ?        00:00:00 ata_aux
 2434 ?        00:00:00 knodemgrd_0
 2437 ?        00:00:00 scsi_eh_0
 2555 ?        00:00:00 scsi_eh_1
 2559 ?        00:00:00 scsi_eh_2
 2615 ?        00:00:00 scsi_eh_3
 2616 ?        00:00:00 scsi_eh_4
 2644 ?        00:02:41 scsi_eh_5
 2648 ?        00:00:00 scsi_eh_6
 2945 ?        00:00:04 kjournald
 3159 ?        00:00:00 udevd
 3715 ?        00:00:00 kpsmoused
 3882 ?        00:00:00 scsi_eh_7
 3889 ?        00:00:22 usb-storage
 8277 ?        00:00:00 drivemount_appl
 9123 ?        00:00:00 scsi_eh_10
 9124 ?        00:00:05 usb-storage
10962 ?        00:00:11 kjournald
10963 ?        00:00:00 kjournald
10964 ?        00:00:00 kjournald
11275 tty4     00:00:00 getty
11276 tty5     00:00:00 getty
11278 tty2     00:00:00 getty
11280 tty3     00:00:00 getty
11282 tty6     00:00:00 getty
11484 ?        00:00:00 acpid
11535 ?        00:00:00 kondemand/0
11536 ?        00:00:00 kondemand/1
11537 ?        00:00:00 kondemand/2
11538 ?        00:00:00 kondemand/3
11618 ?        00:00:00 syslogd
11675 ?        00:00:00 dd
11677 ?        00:00:00 klogd
11699 ?        00:00:03 dbus-daemon
11715 ?        00:00:00 NetworkManager
11729 ?        00:00:00 NetworkManagerD
11742 ?        00:00:00 system-tools-ba
11746 ?        00:00:02 hald
11747 ?        00:00:00 hald-runner
11773 ?        00:00:00 sshd
11790 ?        00:00:00 hald-addon-acpi
11791 ?        00:00:00 hald-addon-hid-
11792 ?        00:00:01 hald-addon-inpu
11794 ?        00:00:00 avahi-daemon
11795 ?        00:00:00 avahi-daemon
11831 ?        00:00:00 cupsd
11867 ?        00:00:03 hald-addon-stor
11869 ?        00:00:03 hald-addon-stor
11871 ?        00:00:03 hald-addon-stor
11873 ?        00:00:03 hald-addon-stor
11875 ?        00:00:03 hald-addon-stor
11881 ?        00:00:21 hald-addon-stor
11886 ?        00:00:08 hald-addon-stor
11932 ?        00:00:00 winbindd
11956 ?        00:00:00 winbindd
11986 ?        00:00:16 dhcdbd
12008 ?        00:00:00 console-kit-dae
12190 ?        00:00:00 hcid
12202 ?        00:00:00 btaddconn
12203 ?        00:00:00 btdelconn
12219 ?        00:00:00 krfcommd
12226 ?        00:00:00 bluetoothd-serv
12248 ?        00:00:00 bluetoothd-serv
12249 ?        00:00:00 gdm
12250 ?        00:00:00 gdm
12272 tty7     02:19:35 Xorg
12288 ?        00:00:00 atd
12307 ?        00:00:00 cron
12330 ?        00:00:00 dhclient
12419 tty1     00:00:00 getty
12512 ?        00:01:53 gconfd-2
12514 ?        00:00:00 gnome-keyring-d
12515 ?        00:00:11 x-session-manag
12636 ?        00:00:00 seahorse-agent
12640 ?        00:00:09 dbus-daemon
12641 ?        00:00:16 gnome-settings-
12678 ?        00:02:46 gnome-panel
12679 ?        00:01:50 gnome-screensav
12700 ?        00:00:00 bonobo-activati
12737 ?        00:00:00 bluetooth-apple
12740 ?        00:00:13 update-notifier
12746 ?        00:00:12 gnome-terminal
12748 ?        00:00:06 devilspie
12749 ?        00:00:00 tracker-applet
12752 ?        00:00:00 trackerd
12756 ?        00:00:11 python
12757 ?        00:04:58 nm-applet
12758 ?        00:00:22 nautilus
12760 ?        00:00:00 gvfsd
12761 ?        00:00:03 gnome-volume-ma
12763 ?        00:00:07 gnome-power-man
12769 ?        00:00:23 gvfs-fuse-daemo
12771 ?        00:00:00 trashapplet
12774 ?        00:00:00 gvfsd-trash
12783 ?        00:00:00 sh
12784 ?        00:00:00 compiz-decorato
12786 ?        00:00:31 gtk-window-deco
12789 ?        00:00:01 mixer_applet2
12795 ?        00:54:52 multiload-apple
12797 ?        00:06:21 sensors-applet
12799 ?        00:00:07 gnome-keyboard-
12801 ?        00:00:06 gweather-applet
12803 ?        00:00:00 gnome-pty-helpe
12804 pts/0    00:00:00 tail
12821 ?        00:00:00 gnome-vfs-daemo
12960 ?        00:01:19 pidgin
13071 ?        00:00:08 notification-da
13519 ?        00:00:00 gvfsd-burn
17838 ?        00:00:00 pdflush
17858 ?        00:00:00 seahorse-daemon
18095 ?        00:00:01 pdflush
19321 ?        00:00:00 scsi_eh_11
19324 ?        00:00:00 usb-storage
19360 ?        00:00:01 hald-addon-stor
21418 ?        00:00:00 compiz
21465 ?        00:11:31 compiz.real
22494 ?        00:00:00 gvfsd-computer
22701 ?        00:00:33 firefox
22735 pts/1    00:00:00 bash
23306 pts/2    00:00:00 bash
23483 pts/1    00:00:00 man
23491 pts/1    00:00:00 pager
23500 pts/2    00:00:00 ps
31545 ?        00:00:00 evolution-data-

```

---

### Post by Yellow Pasque on 2008-08-03
Try upgrading ALSA [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

