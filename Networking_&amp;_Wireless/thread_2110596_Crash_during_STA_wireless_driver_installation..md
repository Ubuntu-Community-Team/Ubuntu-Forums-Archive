---
title: "Crash during STA wireless driver installation."
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by D0wnp0ur on 2013-01-30
I'm new to Linux. I successfully installed Xubuntu 12.04 and proceeded to install the STA driver using "Additional Drivers". During the installation of this driver, the computer screen goes black followed by grey text all over the screen. There was no possible way to navigate this page, so I had to reboot the computer. Upon re-entering Xubuntu, I headed back to "Additional Drivers" and noticed that the STA driver was no longer available to install, yet my networking was still down (in other words, the install didn't work). I'm looking for a fix to this issue. I found another user who had the exact same problem here: [http://ubuntuforums.org/showthread.php?t=2110260](http://ubuntuforums.org/showthread.php?t=2110260)

We both seem to be using the identical, or at least very similar, wireless card. Hopefully somebody will be able to help me out with this.

---

### Post by praseodym on 2013-01-30
Hi,

do you have a wired connection? If yes, open a terminal and reinstall from there:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms patch fakeroot bcmwl-kernel-source
```
Reboot. Check after that:
```
uname -a
lspci -nnk
lsmod
iwconfig
```

---

### Post by D0wnp0ur on 2013-01-30
I managed to do everything that you requested. Everything installed fine.

Here are the results:

```
ashton@Ashton-Latitude-D600:~$ uname -a
Linux Ashton-Latitude-D600 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:04:05 UTC 2012 i686 i686 i386 GNU/Linux
```
```
ashton@Ashton-Latitude-D600:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
    Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500 [8086:4541]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500 [8086:4541]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500 [8086:4541]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
    Subsystem: Dell Latitude D600 [1028:011d]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
    Kernel modules: shpchp
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
    Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
    Subsystem: Intel Corporation Latitude D400/D500 [8086:4541]
    Kernel driver in use: ata_piix
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
    Subsystem: Dell Device [1028:011d]
    Kernel driver in use: snd_intel8x0
    Kernel modules: snd-intel8x0
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
    Subsystem: Conexant Systems, Inc. D480 MDC V.9x Modem [14f1:5422]
    Kernel modules: snd-intel8x0m
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)
    Subsystem: Dell Device [1028:011d]
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
    Subsystem: Dell Device [1028:8126]
    Kernel driver in use: tg3
    Kernel modules: tg3
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
    Subsystem: Dell Device [1028:011d]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
    Subsystem: Dell Device [1028:011d]
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 02)
    Subsystem: Dell Truemobile 1400 [1028:0001]
    Kernel driver in use: wl
    Kernel modules: wl, ssb
```
```
ashton@Ashton-Latitude-D600:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
wl                   3032511  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                733687  2 
pcmcia                 39791  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87213  0 
ttm                    65344  1 radeon
cfg80211              178679  1 wl
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
soundcore              14635  1 snd
lib80211               14040  1 wl
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32114  1 
rfcomm                 38139  16 
bnep                   17830  2 
ppdev                  12849  0 
video                  19068  0 
btusb                  17912  2 
i2c_algo_bit           13199  1 radeon
mac_hid                13077  0 
bluetooth             158438  23 rfcomm,bnep,btusb
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   137273  0 
```
```
ashton@Ashton-Latitude-D600:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by coffeecat on 2013-01-30
@D0wnp0ur, I've added code tags to your terminal output, and split it into four parts to match the four commands. It was unreadable without, mostly because you lose formatting.

Have a look here:

[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

And for BBCode:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

Or the simplest way of adding code tags is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Good luck!

---

### Post by praseodym on 2013-01-31
Which channel does your router send on? Maybe its (still) a bug with channels 12 and 13. Change to a fixed channel between 1-11

---

