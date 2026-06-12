---
title: "HP/Compaq nc8000/Intel PRO/Wireless 2915ABG Not Compatible"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by dellsguy67 on 2010-05-06
I have an nc8000 that gives a "104 unsupported wireless network device detected" error when I plug in my Intel wifi card that I acquired recently. Based on reading, this is a common HP problem due to non-native HP hardware. I am hoping someone can help me to make it work anyway.. :)

If I insert the Intel Pro card after the HP boot screen, 10.04 loads just fine and Ubuntu detects the card. I will fill in the info below, and hopefully someone is familiar w/ making this work. 

Thanks!

1 ) Machine Brand and Model (PC/Laptop):

HP/Compaq nc8000

2 ) Wireless Brand, Model and Wireless Chipset:

02:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)


3 ) check interface:
Code:

eth0      Link encap:Ethernet  HWaddr 00:08:02:f3:00:73  
          inet addr:192.234.197.10  Bcast:192.234.197.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fef3:73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3210116 (3.2 MB)  TX bytes:264734 (264.7 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:de:72:b1  
          inet6 addr: fe80::20e:35ff:fede:72b1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:220 (220.0 B)
          Interrupt:11 Base address:0xc000 Memory:90010000-90010fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


4 ) Check for modules:
Code:
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
radeon                674135  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162471  4 radeon,ttm,drm_kms_helper
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia                 33024  0 
lp                      7028  0 
i2c_algo_bit            5028  1 radeon
ipw2200               135216  0 
joydev                  8708  0 
yenta_socket           20408  3 
rsrc_nonstatic         10015  1 yenta_socket
ppdev                   5259  0 
soundcore               6620  1 snd
libipw                 39896  1 ipw2200
parport_pc             25962  1 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
parport                32635  3 lp,ppdev,parport_pc
smsc_ircc2             16977  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lib80211                5046  2 ipw2200,libipw
shpchp                 28820  0 
intel_agp              24177  1 
video                  17375  0 
psmouse                63245  0 
agpgart                31724  3 ttm,drm,intel_agp
serio_raw               3978  0 
output                  1871  1 video
irda                  186556  1 smsc_ircc2
crc_ccitt               1339  1 irda
ohci1394               26950  0 
tg3                   109292  0 
ieee1394               81181  1 ohci1394
floppy                 53016  1 


6 ) Network configuration
Code:

$   *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:de:72:b1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:11 memory:90010000-90010fff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 03
       serial: 00:08:02:f3:00:73
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5705-v3.14 ip=192.234.197.10 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:90000000-9000ffff memory:4c000000-4c00ffff(prefetchable)


7 ) Scan for networks:
Code:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results


8 ) Ubuntu Version:
Code:
Ubuntu 10.04 LTS

9 ) Kernel/architecture (including 32 vs. 64 bit):
Code:

2.6.32-21-generic i686

---

### Post by chili555 on 2010-05-06
The good news is that the Intel 2915ABG is well supported and works well. I am quite confident that if you detached the ethernet cable to let Network manager manage your connection, you would easily connect. I have installed one in a Thinkpad T40 after I overcame the same error; in IBM speak it's an 1802 error.

The bad news is that the fix is not easy and dangerous.

[http://www.rechner.org/b1800_bios.html](http://www.rechner.org/b1800_bios.html)

[http://www.richud.com/HP-Pavilion-104-Bios-Fix/](http://www.richud.com/HP-Pavilion-104-Bios-Fix/)> HP/Compaq as well as DELL and other manufacturers built a whitelist of allowed vendor ID's into their BIOS. As a result you can only use "their" cards and accessories which usually come with a price premium. When trying to use a 3rd party card you will only get the infamous 104-Unsupported wireless network device detected error message and the notebook will refuse to boot. This guide will show you how to modify the BIOS Oh, momma!!

I am sure if you Google around, you can find the fix for your exact model. Good luck.

---

### Post by dellsguy67 on 2010-05-06
Chili - you helped fix another laptop I have. 10.04 on a dell d820. the wifi continuously dropped and reconnected and one of your posts contained suggestions, one of which worked after a lot of struggles. 

I will check out those links. It would appear altering the bios isn't as clear cut as i'd hoped, unless someone else here knows otherwise.

---

