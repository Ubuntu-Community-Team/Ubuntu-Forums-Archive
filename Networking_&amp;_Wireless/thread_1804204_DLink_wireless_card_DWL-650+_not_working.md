---
title: "DLink wireless card DWL-650+ not working"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by LenK on 2011-07-14
Laptop with Intel PIII Lubuntu 11.04

The card is listed as needing the ACX100 driver. From Sourceforge I downloaded acx-20080210.tar.bz2

Summary on the download page:
*Open Source Linux driver for wireless network cards (DWL-[G]520+ PCI, DWL-[G]650+ CardBus, GL-2422MP mini-PCI, DWL-120+ USB etc.) which use the entirely undocumented Texas Instruments (TI) ACX100/ACX111 chips, for 2.4.x to 2.6.x kernels. FreeBSD: see htt*

ASSUMING that all is well with the above, ie. the driver is required and I have the correct one, how do I install the above file?

IF NOT, where is the problem?

System info...

$ lspci
Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface

$ lsusb - terminal went off down the yellow brick road (no response)

$ ifconfig (did not copy eth0)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ lsmod
Module                  Size  Used by
usb_storage            43946  0 
uas                    17676  0 
dm_crypt               22463  0 
vesafb                 13449  1 
snd_via82xx_modem      18305  0 
snd_maestro3           22973  1 
snd_ac97_codec        105614  2 snd_maestro3,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_maestro3,snd_via82xx_modem,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
yenta_socket           27230  0 
snd                    55295  10 snd_via82xx_modem,snd_maestro3,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
via686a                19446  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
parport_pc             32111  1 
i2c_viapro             12969  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_via82xx_modem,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
8139too                23208  0 
firewire_ohci          31504  0 
8139cp                 22497  0 
firewire_core          56138  1 firewire_ohci
floppy                 60032  0 
pata_via               13368  2 
crc_itu_t              12627  1 firewire_core

$ dmesg | grep "wlan" - no results

$ sudo lshw -C network
[sudo] password for len: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:90:f5:03:d0:a6
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.0.105 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:10 ioport:1400(size=256) memory:f0004800-f00048ff
  *-network UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: ioport:2800(size=32) memory:2c010000-2c010fff memory:2c000000-2c00ffff

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

$ uname -mr
2.6.38-10-generic i686

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...

---

