---
title: "Broadcom 4401 - Ethernet not functioning"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by mcm15901 on 2011-07-25
I'm trying to help a friend who needs her Ethernet to work on a Dell Inspiron E1505 laptop running Linux Mint 10 (essentially Maverick), kernel 2.6.35-22-generic. The b44 driver does load and the system sees the card but there is no communication going through it. A thorough search of these forums hasn't yielded a sure answer yet.

I have disabled the wireless component of this card in BIOS and uninstalled the several modules tied to the Broadcom 43xx wireless cards. The Ethernet port is still not communicating.

Here's some Terminal output:

```
stephie@stephie-MM061 ~ $ dmesg | grep eth0
[    1.333301] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:cf:15:e4
[   20.086186] ADDRCONF(NETDEV_UP): eth0: link is not ready

stephie@stephie-MM061 ~ $ lspci -nn | grep -i bcmlspci -nn |grep -i bcm4401
stephie@stephie-MM061 ~ $ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common

stephie@stephie-MM061 ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:cf:15:e4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6648 (6.6 KB)  TX bytes:6648 (6.6 KB)

ppp0      Link encap:Point-to-Point Protocol  <snip, this is the only working Internet connection here>

stephie@stephie-MM061 ~ $ sudo lshw -C network
[sudo] password for stephie: 
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:cf:15:e4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff

stephie@stephie-MM061 ~ $ lsmod
Module                  Size  Used by
ppp_deflate             3726  0 
bsd_comp                4791  0 
ppp_async               6778  1 
crc_ccitt               1351  1 ppp_async
sierra                  9487  1 
usbserial              33100  4 sierra
nls_iso8859_1           3261  2 
nls_cp437               4931  2 
vfat                    9201  2 
fat                    48240  1 vfat
aes_i586                7280  325 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
joydev                  8735  0 
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                2852  0 
dell_laptop             5730  0 
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
dcdbas                  5402  1 dell_laptop
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    18877  2 sm_common,nand
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  2 ppp_deflate,btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
radeon                825934  3 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
drm                   168054  5 radeon,ttm,drm_kms_helper
usb_storage            40172  2 
b44                    26253  0 
firewire_ohci          21106  0 
intel_agp              26360  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
ssb                    39288  1 b44
firewire_core          46643  1 firewire_ohci
led_class               2633  1 sdhci
video                  18712  0 
mii                     4425  1 b44
crc_itu_t               1383  1 firewire_core
i2c_algo_bit            5168  1 radeon
agpgart                32011  3 ttm,intel_agp,drm
output                  1883  1 video

stephie@stephie-MM061 ~ $ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:15:c5:cf:15:e4
Sending on   LPF/eth0/00:15:c5:cf:15:e4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```Any ideas on how to get this Ethernet port willing to talk?

---

