---
title: "Can't connect to recognized wireless network"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by wavery on 2010-07-01
Hi,
I upgraded to 10.04 from 9.10.  I had no problem connecting to my wireless network with 9.10, but can't with 10.04.  The network shows up as available, but it won't connect when I enter the security information.  Below are the details and the information I've seen requested from others with a similar problem.  Any help would be greatly appreciated...I'm at my wits end.

Dell Inspiron 8200 Laptop with TrueMobile 1150 wireless card.


will@will-laptop:~$ sudo lshw -c network 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:3e:0b:7c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:48000000-4801ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 1
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:75:0e:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b


will@will-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller


will@will-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"hyjinx"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:5  Rx invalid frag:8
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



will@will-laptop:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
michael_mic             1732  4 
ch7006                 16373  1 
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126485  1 orinoco
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
pcmcia                 33024  1 orinoco_cs
joydev                  8708  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 nouveau
drm_kms_helper         29297  2 ch7006,nouveau
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  4 
drm                   162471  5 ch7006,nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
dell_wmi                1793  0 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
soundcore               6620  1 snd
dcdbas                  5422  0 
intel_agp              24177  1 
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_rng               2276  0 
shpchp                 28820  0 
agpgart                31724  3 ttm,drm,intel_agp
ppdev                   5259  0 
video                  17375  0 
output                  1871  1 video
parport_pc             25962  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
3c59x                  31839  0 
mii                     4381  1 3c59x
ieee1394               81181  1 ohci1394
floppy                 53016  0 
usbhid                 36110  0 
hid                    67032  1 usbhid

---

### Post by wavery on 2010-07-07
Bump...anything?

---

### Post by Wangsta on 2010-07-07
So I have a somewhat similar problem.

I installed Ubuntu 10.04 on a dual booted XP computer, and I have been connecting to the internet fine.  However recently, and all of a sudden, I just can't. All the routers are still displayed with their active signal strength and stuff, but I when I try to connect, it just says "connecting" but never connects and eventually says "disconnected."

Also, the windows XP part of my computer still connects fine. Sadly, I've been forced to use windows for more than a week, and it's starting to hurt.  :cry: Somebody help!

I'm sorry for such a vague problem, but it's been fine up until now. what happened?

---

### Post by chandra on 2010-07-07
Try installing wicd instead
```
sudo apt-get install wicd
```
and see if it solves your problem.

---

### Post by wavery on 2010-08-16
Not having any luck making a wireless connection with 10.04.  Before I revert back to 9.10, I'm thinking about trying a new wireless card.  Anyone have an opinion on whether that might help or not?  Thanks!

---

