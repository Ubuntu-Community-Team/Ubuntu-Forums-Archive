---
title: "Wireless Connection"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by jrb368 on 2009-11-24
Hi,

I'm trying to get my wireless connection established on my laptop.  I've gone through several of the threads regarding this topic, but I can't seem to get it fixed (or maybe I'm just one step away).  Please reference the following outputs.  Thanks!

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:0b:db:dd:5c:08  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fedd:5c08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:715922 (715.9 KB)  TX bytes:133103 (133.1 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.
```lsmod:

```
Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
pcmcia                 36808  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           24200  4 
rsrc_nonstatic         11644  1 yenta_socket
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               7264  1 snd
ppdev                   6688  0 
iptable_filter          3100  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
joydev                 10272  0 
shpchp                 32272  0 
parport_pc             31940  1 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
psmouse                56500  0 
serio_raw               5280  0 
dell_wmi                2564  0 
dcdbas                  7292  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
tg3                   109600  0 
video                  19380  0 
output                  2780  1 video
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp
```lspci:

```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by northd_tech on 2009-11-24
Hi jrb,

This appears to be your "WiFi critter:"

[COLOR=Blue]02:03.0 Network controller: **Broadcom** Corporation **BCM4306** 802.11b/g Wireless LAN Controller (rev 02)

[COLOR=Black]I believe that the 4306 is the older "legacy" "b43" Broadcom, but don't quote me on that (do some research on "Broadcom 4306 linux driver")

I was just helping someone with a Broadcom "4311," and I believe that has the same "STA" fix that yours needs (and my HP with Broadcom 4321AG also needs).

Corporate laziness/efficiency can be a beautiful thing at times.;)

You might want to look at this thread:

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

[/COLOR][/COLOR]

---

