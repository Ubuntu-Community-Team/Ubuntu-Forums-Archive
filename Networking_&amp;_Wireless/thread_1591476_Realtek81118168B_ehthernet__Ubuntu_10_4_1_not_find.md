---
title: "Realtek8111/8168B ehthernet / Ubuntu 10 4 1 not finding wireless network"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by toussaint on 2010-10-09
[FONT=Arial][SIZE=2]I installled Ubuntu 10.4.1 on a brand new computer with a Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller on a Foxconn G41MXE motherboard. and I have been unable to connect to wireless network. 

I have gone through the wireless trouble shooting guide to no avail. When i "check for device recognition" i get the following (note the is no CLAIMED UNCLAIMED ENABLED OR DISABLED)

udo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 90:fb:a6:42:3d:c2
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)

I have read "how to post a wireless issue" ( as well as going dizzy searching forums and documents to find a solution myself) and the following info might assist you in helping me. Please tell me if i need provide any other information.[/SIZE][/FONT]                                  [FONT=Arial][SIZE=2]**Wireless Brand, Model and Wireless Chipset**[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**Device Recognition**[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]sudo lshw -C network  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]  *-network                [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       description: Ethernet interface  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       product: RTL8111/8168B PCI Express Gigabit Ethernet controller  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       vendor: Realtek Semiconductor Co., Ltd.  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       physical id: 0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       bus info: pci@0000:02:00.0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       logical name: eth0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       version: 03  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       serial: 90:fb:a6:42:3d:c2  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       size: 10MB/s  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       capacity: 1GB/s  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       width: 64 bits  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       clock: 33MHz  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**ifconfig **[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]eth0      Link encap:Ethernet  HWaddr 90:fb:a6:42:3d:c2   [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          inet6 addr: fe80::92fb:a6ff:fe42:3dc2/64 Scope:Link  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          RX packets:20141 errors:0 dropped:0 overruns:0 frame:0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          TX packets:12854 errors:0 dropped:0 overruns:0 carrier:0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:1000  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          RX bytes:13337249 (13.3 MB)  TX bytes:2026548 (2.0 MB)  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          Interrupt:26 Base address:0xe000  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]lo        Link encap:Local Loopback   [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          inet addr:127.0.0.1  Mask:255.0.0.0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          inet6 addr: ::1/128 Scope:Host  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          UP LOOPBACK RUNNING  MTU:16436  Metric:1  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          RX packets:12 errors:0 dropped:0 overruns:0 frame:0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          collisions:0 txqueuelen:0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**iwconfig**[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]lo        no wireless extensions.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]eth0      no wireless extensions.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**lsmod **[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Module                  Size  Used by  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]aes_i586                7268  358  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]aes_generic            26863  1 aes_i586  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]binfmt_misc             6587  1  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]dm_crypt               11331  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_hda_codec_realtek   203310  1  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_hda_intel          21941  2  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_hwdep               5412  1 snd_hda_codec  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_pcm_oss            35308  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_mixer_oss          13746  1 snd_pcm_oss  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_seq_dummy           1338  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_seq_oss            26726  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_seq_midi            4557  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_rawmidi            19056  1 snd_seq_midi  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_timer              19098  2 snd_pcm,snd_seq  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]ppdev                   5259  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]parport_pc             25962  1  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]lp                      7028  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]psmouse                63245  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]serio_raw               3978  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]soundcore               6620  1 snd  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]snd_page_alloc          7076  2 snd_hda_intel,snd_pcm  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]parport                32635  3 ppdev,parport_pc,lp  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]fbcon                  35102  71  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]tileblit                2031  1 fbcon  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]font                    7557  1 fbcon  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]bitblit                 4707  1 fbcon  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]softcursor              1189  1 bitblit [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]vga16fb                11385  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]vgastate                8961  1 vga16fb [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]usbhid                 36110  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]hid                    67032  1 usbhid  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]i915                  285076  3  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]drm_kms_helper         29297  1 i915  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]drm                   162377  4 i915,drm_kms_helper  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]r8169                  34076  0  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]mii                     4381  1 r8169  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]intel_agp              24119  2 i915  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]agpgart                31724  2 drm,intel_agp  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]i2c_algo_bit            5028  1 i915  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]video                  17375  1 i915  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]output                  1871  1 video  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**uname -mr **[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]2.6.32-24-generic i686  [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]sudo /etc/init.d/networking restart  [/SIZE][/FONT]
   
 [FONT=Arial][SIZE=2] * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.[/SIZE][/FONT]
 

Thankyou for your help

---

### Post by bkratz on 2010-10-09
The Realtek RTL8111/8168B PCI Express Gigabit Ethernet controller  is your wired connection, not the wireless.

You might look at 

lspci -nn

and see if anything looks like the wireless device, might say something like network or wireless or just post the output.


Also, if the problem is with your wired connection, you might look at the following

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)

---

### Post by toussaint on 2010-10-09
I guess i have exposed the level of my ignorance:)
lspci nn gave me the following. Which is my wireless adapter. Wired connection is no problem by the way

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e30] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)

---

### Post by bkratz on 2010-10-09
well I don't see it anywhere. Could it be a usb device? You might post the contents of 

lsusb

also.

In your first post you said " Please tell me if i need provide any other information. Wireless Brand, Model and Wireless Chipset". Do you have any idea or the part number of your computer. You might also check the bios at powerup to make sure the wireless card is enabled.

Also you might look at 

rfkill list

and see if it says yes to either "softblocked or hardblocked"

---

### Post by toussaint on 2010-10-09
No it is not a usb device. The computer is a Novatech Isys PC1409

 

 Lsusb
 

 Bus 005 Device 002: ID 0461:4d64 Primax Electronics, Ltd  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 002: ID 04f2:0112 Chicony Electronics Co., Ltd KU-8933 Keyboard with PS/2 Mouse port  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

 $ rfkill  
 Usage:	rfkill [options] command  
 Options:  
 	--version	show version (0.4)  
 Commands:  
 	help  
 	event  
 	list [IDENTIFIER]  
 	block IDENTIFIER  
 	unblock IDENTIFIER  
 where IDENTIFIER is the index no. of an rfkill switch or one of:  
 	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm 



I went into BIOS but a bit unsure what to look for. I saw nothing which obviously related to wireless card . Under Onboard configuration I found Audio controller enabled , LAN controller enabled ,LAN boot ROM disabled.


Thanks very much for your help on this

---

### Post by bkratz on 2010-10-09
I have googled, googlubuntu and gone to the website of Novatech and have come up empty. The Novatech forum has some wireless postings, but everyone had added card (all different too). Are you sure it has one? Sorry, just frustrated! Will still continue to look.

---

### Post by toussaint on 2010-10-10
I will call Novatech Tech support tomorrow(closed today) and hopefully they will identify the wireless card. Could they really be selling a pc without wireless capabilities? I hope not.
Please advise me of any other action i might make. 
Thanks again for your help

---

### Post by toussaint on 2010-10-11
I just spoke to novatech who confirmed there is no wireless card. I'm am very sorry to have wasted your time. Thanks

---

