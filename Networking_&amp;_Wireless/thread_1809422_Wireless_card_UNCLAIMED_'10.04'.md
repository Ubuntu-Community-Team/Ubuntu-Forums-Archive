---
title: "Wireless card UNCLAIMED '10.04'"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by moonsal on 2011-07-21
I'm on my ubuntu box via wired network trying to install my wireless card with no luck.. My wireless device is "Unclaimed"??? Meaning no driver was loaded?? Installed ndis and applied my windows driver but to no avail.. Some help would be appreciated... Thanks BTW my chipset it bcm4318 (not listed in the tuts)...

```

lshw -C network
 *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:01:0e.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:f4102000-f4103fff

```

```

lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```


No wlan0.... 
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:c5:c1:73:e4  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:c5ff:fec1:73e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2221806 (2.2 MB)  TX bytes:237970 (237.9 KB)
          Interrupt:9 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


```

---

### Post by nm_geo on 2011-07-21
Please copy and paste in terminal

```
lspci -nn | grep 0280
```

```
rfkill list all
```

```
lsmod
```

That will get us going..

---

### Post by moonsal on 2011-07-21
Here we go.....

```
lspci -nn | grep 0280
01:0e.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```'rfkill list all' just returns to prompt..

```
lsmod
Module                  Size  Used by
i810                   16400  2 
drm                   162377  3 i810
ppdev                   5259  0 
snd_intel8x0           25652  6 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  3 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
fbcon                  35102  71 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
bitblit                 4707  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
softcursor              1189  1 bitblit
ndiswrapper           184677  0 
snd                    54244  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  3 snd
vga16fb                11385  1 
shpchp                 28835  0 
vgastate                8961  1 vga16fb
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
lp                      7028  0 
intel_agp              24375  1 
parport                32635  2 ppdev,lp
agpgart                31724  3 drm,intel_agp
usbhid                 36110  0 
8139too                18545  0 
hid                    67288  1 usbhid
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp

```

---

### Post by moonsal on 2011-07-21
OK, problem solved..... Ignorance on my part, through ndis I hadn't copied the driver over from my usb and got to carried away....  Thanks for your willingness to help maan...

---

### Post by nm_geo on 2011-07-21
No Problem ..

In the future if you keep that box b43-fwcutter and firmware-b43-installer will work too.

---

### Post by moonsal on 2011-07-21
Roger that... Thanks.... I'd rather have the b43 firmware but my package manager wouldn't find it... This will be DANDY for now though....

---

### Post by guliminipietro on 2012-10-15
I have the same problem with intel 8086, I would appreciate it if you give me a help

---

