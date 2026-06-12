---
title: "No Connection"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by aNGaJe on 2010-02-14
I am living at student hostel and we got cable connections.When i tried to set my LAN connection, it says got connection established but i can not join anywebpage or network comp. as like on pictures.
1st
[img]http://img716.imageshack.us/img716/2914/screenshotbw.png[/img]
2nd
[img]http://img12.imageshack.us/img12/559/screenshot1yg.png[/img]
can anyone help me about it ?

---

### Post by northd_tech on 2010-02-14
Hi [aNGaJe]("http://ubuntuforums.org/member.php?u=673482"),

We need to find out a little about your hardware and how it is currently set up.  Can you open a terminal window and enter the following commands in ubuntu?  

It won't matter whether if you have internet to enter the commands, but of course you will need internet to post the results, so you might want so save those results in a text file on a USB stick using either the Kate or gedit text editor if you need to use another internet connection to post the results.

The command to open gedit from a terminal (if it's installed) is simply:

```
gedit &
```

These are those commands to enter in the terminal window:

```
lspci

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig
```

That "sudo lshw" command will want your administrator password (usually the same as your main login password unless you've set up multiple user accounts).

---

### Post by aNGaJe on 2010-02-14
```

00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge (rev 01)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3870
01:00.1 Audio device: ATI Technologies Inc Radeon HD 3870 Audio device
04:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
04:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
07:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```
```

Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
zl10036                 5504  1 
snd_hwdep               7200  1 snd_hda_codec
mt312                   7680  1 
saa7134_alsa           12128  1 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_pcm_oss
saa7134_dvb            22760  0 
videobuf_dvb            7040  1 saa7134_dvb
dvb_core               87364  1 videobuf_dvb
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0 
saa7134               152616  2 saa7134_alsa,saa7134_dvb
snd_timer              22276  2 snd_pcm,snd_seq
ir_common              48512  1 saa7134
v4l2_common            17500  1 saa7134
videodev               36736  2 saa7134,v4l2_common
v4l1_compat            14496  1 videodev
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videobuf_dma_sg        12544  3 saa7134_alsa,saa7134_dvb,saa7134
ip_tables              11692  1 iptable_filter
soundcore               7264  1 snd
ppdev                   6688  0 
x38_edac                4484  0 
videobuf_core          17952  3 videobuf_dvb,saa7134,videobuf_dma_sg
psmouse                56180  0 
x_tables               16544  1 ip_tables
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
edac_core              40176  2 x38_edac
parport_pc             31940  1 
tveeprom               11872  1 saa7134
serio_raw               5280  0 
parport                35340  3 ppdev,lp,parport_pc
btusb                  11856  2 
radeon                636000  1 
ohci1394               29900  0 
floppy                 54916  0 
ieee1394               86596  1 ohci1394
ttm                    36212  1 radeon
r8169                  32064  0 
drm                   159584  3 radeon,ttm
mii                     5212  1 r8169
agpgart                34988  2 ttm,drm
i2c_algo_bit            5760  1 radeon

```
```

Linux angaje-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```
```

angaje@angaje-desktop:~$ sudo lshw -C network
[sudo] password for angaje: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:7d:03:1d:79
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:c000(size=256) memory:e8010000-e8010fff(prefetchable) memory:e8000000-e800ffff(prefetchable) memory:e8020000-e802ffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: 00:1d:7d:03:1d:7b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=77.71.59.15 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:d000(size=256) memory:e8210000-e8210fff(prefetchable) memory:e8200000-e820ffff(prefetchable) memory:e8220000-e822ffff(prefetchable)

```
```

angaje@angaje-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:03:1d:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1d:7d:03:1d:7b  
          inet addr:77.71.59.15  Bcast:77.71.59.127  Mask:255.255.255.128
          inet6 addr: fe80::21d:7dff:fe03:1d7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:170528 (170.5 KB)  TX bytes:98825 (98.8 KB)
          Interrupt:31 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```

angaje@angaje-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by northd_tech on 2010-02-14
> **aNGaJe said:**
> ```

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

That seems a little odd to me that the Realtek 8111/8168B ethernet is being assigned 2 different PCI addresses- that might indicate a conflict.  The **lshw** command makes it look like one is 10 MB/sec and one is 100 MB/sec (which might be normal for that card- I've never worked with one of those before, so I can't say for sure).

In a quick scan of the **lsmod** results, I didn't see any Realtek modules loaded (which would be a big problem for ethernet).  That 2.6.28-14 is getting to be one of the older kernels, but it was one of the more stable/reliable from my experience.  Unfortunately it sounds like that "-14" kernel does not have built-in support for your Realtek ethernet card.

I don't guess you have the option to boot another kernel (hopefully -16, -17, -18, or -19 depending upon your ubuntu version 9.04 or 9.10)?  One of those might have better support for that Realtek card.

Reading through some old threads, that network interface (NIC) was kind of erratic with the older kernels:

**Ubuntu Server 8.04.2 & Realtek 8111/8168B Network**
[http://ubuntuforums.org/showthread.php?t=1129293&highlight=realtek+8111%2F8168B](http://ubuntuforums.org/showthread.php?t=1129293&highlight=realtek+8111%2F8168B)

**Realtek 8168/8111 network problem (dual-boot)**
[http://ubuntuforums.org/showthread.php?t=1059393&highlight=realtek+8111%2F8168B](http://ubuntuforums.org/showthread.php?t=1059393&highlight=realtek+8111%2F8168B)

Here is a newer thread about that NIC that makes it sound like it needs the Realtek "r8169" module to work (post #6):

Network problem
[http://ubuntuforums.org/showthread.php?t=1350212&highlight=realtek+8111%2F8168B](http://ubuntuforums.org/showthread.php?t=1350212&highlight=realtek+8111%2F8168B)

I don't guess you know anyone who would have access to a newer version of Ubuntu (or could download a newer LiveCD) that you could test out?

---

### Post by aNGaJe on 2010-02-14
I dont think its about realtek cos. i was using it when i was at rent. When i changed my connection type {moved student hostel} it couldnt connect internet :(

---

### Post by northd_tech on 2010-02-14
> **aNGaJe said:**
> 
Module                  Size  Used by

**r8169 **                 32064  0 
drm                   159584  3 radeon,ttm
mii                     5212  1 **r8169**

[/code]
```

Linux angaje-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 **i686** GNU/Linux

```

It does look like the "r8169" module is loaded into the ubuntu kernel (but I'm not sure if there should be something else there).

If it makes a difference, you are running a 32-bit "i686" version of ubuntu (which is good, since 64-bit often creates a lot more problems).  You will want to watch for 32-bit fixes in those "realtek 8111" threads here.

Good luck.

---

### Post by northd_tech on 2010-02-14
Do you have 2 places to physically plug in a network cable on the computer?  (One on the motherboard and one on an expansion card maybe).  From what I read on those other threads, those 2 Realtek PCI addresses don't look right to me in that **lspci** command (and there is only one module loaded apparently).

Unfortunately, that's not one of the Realtek interfaces that I've worked with before (I have worked with their wireless stuff quite a bit).

---

### Post by aNGaJe on 2010-02-14
i got bluetooth device and satellite card. Both of them creates LAN connection on Windows. But not realtek :( =/ lets wait another ideas

---

### Post by aNGaJe on 2010-02-17
any idea ?

---

