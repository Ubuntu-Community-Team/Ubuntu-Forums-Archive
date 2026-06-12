---
title: "Lan not working on fresh install"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by PinguinMalin on 2010-10-30
Hello, I just installed ubuntu 10 on my pc and unfortunatly I don't have internet. I only have one pc wired to my 2wire modem. I want to use dhcp, no static ip if possible.

here's the modem information.
gateway 192.168.2.1
mask 255.255.255.0
DHCP range 192.168.2.10 - 192.168.2.254

Here my pc informations

root@meow:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:73:8c:b8  
          inet6 addr: fe80::92e6:baff:fe73:8cb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113907 (113.9 KB)  TX bytes:10530 (10.5 KB)
          Interrupt:44 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:06:4f:4c:db:dc  
          inet6 addr: fe80::206:4fff:fe4c:dbdc/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3940 (3.9 KB)  TX bytes:291209 (291.2 KB)
          Interrupt:21 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:95724 (95.7 KB)  TX bytes:95724 (95.7 KB)

root@meow:~# lsmod
Module                  Size  Used by
iptable_filter          1778  0 
ip_tables              19107  1 iptable_filter
x_tables               24423  2 iptable_filter,ip_tables
nls_utf8                1453  1 
isofs                  34218  1 
parport_pc             30086  0 
ppdev                   6804  0 
binfmt_misc             7984  1 
snd_hda_codec_realtek   299533  1 
snd_usb_audio         105727  1 
snd_usbmidi_lib        21313  1 snd_usb_audio
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  2 snd_usb_audio,snd_hda_codec
snd_pcm                89104  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
nouveau               568848  2 
snd_seq_midi            5932  0 
snd_seq_midi_event      7291  1 snd_seq_midi
uvcvideo               62379  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
ttm                    68212  1 nouveau
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
snd_timer              23850  2 snd_pcm,snd_seq
drm_kms_helper         32836  1 nouveau
snd_seq_device          6912  3 snd_seq_midi,snd_seq,snd_rawmidi
v4l2_compat_ioctl32    12646  1 videodev
joydev                 11363  0 
asus_atk0110           12987  0 
snd                    64117  17 snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
psmouse                62080  0 
i2c_piix4              10047  0 
edac_core              46822  0 
edac_mce_amd            9387  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
k10temp                 3535  0 
drm                   206161  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6208  1 nouveau
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
hid                    84678  1 usbhid
floppy                 65299  0 
r8169                  42222  0 
mii                     5261  1 r8169
pata_atiixp             4405  1 
ahci                   21857  0 
libahci                26167  3 ahci
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core

root@meow:~# lspci
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:11.0 RAID bus controller: ATI Technologies Inc SB700/SB800 SATA Controller [RAID5 mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
root@meow:~# gedit /etc/network/i
if-down.d/      if-post-down.d/ if-pre-up.d/    if-up.d/        interfaces      
root@meow:~# gedit /etc/network/interfaces 
root@meow:~# more /etc/network/interfaces 
auto lo
iface lo inet loopback

routes: command not found
root@meow:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

root@meow:~# dmesg | grep eth
[    1.508194] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xffffc900110ae000, 90:e6:ba:73:8c:b8, XID 18000000 IRQ 44
[    1.510638] r8169 0000:01:06.0: eth1: RTL8169sb/8110sb at 0xffffc90011094c00, 00:06:4f:4c:db:dc, XID 10000000 IRQ 21
[    7.422433] r8169 0000:03:00.0: eth0: link down
[    7.422789] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.644175] r8169 0000:01:06.0: eth1: link up
[   18.580037] eth1: no IPv6 routers present
[42598.359536] r8169 0000:01:06.0: eth1: link down
[42604.117825] r8169 0000:03:00.0: eth0: link up
[42604.118151] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[42614.480076] eth0: no IPv6 routers present


If you need more information ask me in new to networking.

Best regard

---

### Post by P4man on 2010-10-30
I see you logged in as root, is this ubuntu server install or a regular install using gnome and network-manager  ?
Also, whats the output of

```
sudo dhclient
```

Last point; you seem to have 2 nics in there. Have you tried connecting to the other? DHCP is the default setting, you shouldnt have to do anything for it.

---

### Post by PinguinMalin on 2010-10-30
ok, thanks for replying.

This is the normal install. I use gnome, but I have no success up to now with the network manager ( System/Preference/Network Connection or System/Administration/Network Tools).

I have indeed two network cards. I installed the second one to make sure it wasn't a hardware problem. At the moment the wire is plugged in eth1.

For the output of dhclient

There is already a pid file /var/run/dhclient.pid with pid 2076
killed old client process, removed PID file.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit  [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth1/00:06:4f:4c:db:dc
Sending on LPF/eth1/00:06:4f:4c:db:dc
Listening on LPF/eth0/90:e6:ba:73:8cb8
Sending on LPF/eth0/90:e6:ba:73:8cb8
Sending  on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 on interval 3
DHCPREQUEST of 192.168.2.13 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.13 from 192.168.2.1
bound to 192.168.2.13 - - rebewal in 117442 seconds.

I don't know if this help, the last line contains the ip of my gateway (192.168.2.1). 

Also maybe this will help,

After I did what you asked my Internet started working. >_<

---

### Post by P4man on 2010-10-30
Are you logging in as root? Perhaps the network is only configured for your normal user. I dont know how new you are to ubuntu, but logging in as root is almost always a very bad idea. If you copy/pasted those commands after running sudo -i then disregard the above. Then for some reason dhclient isnt or wasnt getting an ip. Let me know if it persists after a reboot.

---

### Post by PinguinMalin on 2010-11-01
Hi, 

No I'm not logging in as root. I upped myself to root because I felt like it, you know sometime you fell like being root will resolve the problem :P. 

It is **persistent **each time I boot my machine I need to run the command dhclient. It does the same thing in windows XP so I suspect the cable to give me a weak signal and I miss some important initializing packets (or maybe it's the **cosmic rays**' fault !). 

I don't have a second 50' cat5 RJ45 cable to test and this is probably not anymore the good sub-forum to ask the question : How to know I have a good cable ? Thanks I'll try to put this solved.

---

### Post by P4man on 2010-11-01
Windows does the same? Hmmm.. I wouldnt blame the cable, DHCP is only a few packets, I cant see them getting lost every boot while normal network operation would not cause havoc. Id rather suspect your router (or modem or whatever acts as DHCP server).

---

