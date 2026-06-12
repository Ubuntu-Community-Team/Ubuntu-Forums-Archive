---
title: "Wireless problem on Lucid Lynx 64 bits, Dell laptop"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by Wallion on 2010-08-25
Good evening everybody,

First of all, I'm from Belgium and I want to apologize if my English is not good enough, I'll try to do my best.
And now, here's my problem :

I bought a new Dell laptop one week ago and decide to install Ubuntu 10.4 in place of Win7. First I tried the live version and my WIFI card was correctly working. So I installed Ubuntu on my HD but then, my WIFI card wasn't working anymore and I don't know why...

So, I hope that one of you know what's wrong ! (for instance, I'm using a USB device from D-link to be on internet)

**1) Laptop model**
```
Dell Studio 1749
```

**2) lspci**
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
14:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
14:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
14:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
20:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

**3a) ifconfig eth1 (my wifi card)**
```
eth1      Link encap:Ethernet  HWaddr 78:e4:00:b3:67:2c  
          adr inet6: fe80::7ae4:ff:feb3:672c/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17 

```

**3b) iwconfig eth1**
```
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc
```

**4) lsmod**
```
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
usb_storage            49833  0 
rt2870sta             628043  1 
joydev                 11072  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_idt      61450  1 
snd_seq_dummy           1782  0 
snd_hda_intel          25677  6 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_seq_oss            31219  0 
snd_hwdep               6924  1 snd_hda_codec
snd_seq_midi            5829  0 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_rawmidi            23420  1 snd_seq_midi
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip     8676  0 
snd                    71106  24 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
dell_wmi                2177  0 
fbcon                  39270  75 
tileblit                2487  1 fbcon
psmouse                64576  0 
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
serio_raw               4918  0 
softcursor              1565  1 bitblit
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
dell_laptop             7941  0 
dcdbas                  6886  1 dell_laptop
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
fglrx                2353422  106 
sdhci_pci               6700  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
sdhci                  17928  1 sdhci_pci
led_class               3764  1 sdhci
intel_agp              29095  0 
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
r8169                  39650  0 
mii                     5237  1 r8169
ahci                   37870  2 
ieee1394               94771  1 ohci1394
```

**5) dmesg | grep eth1**
```
[   13.866917] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 
[   24.863045] eth1: no IPv6 routers present
[18446744073.535541] eth1: no IPv6 routers present
[    0.029096] eth1: no IPv6 routers present

```

**6 ) Network configuration**
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 78:e4:00:b3:67:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:20:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:ea:52:39
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:36 ioport:5000(size=256) memory:f0404000-f0404fff(prefetchable) memory:f0400000-f0403fff(prefetchable) memory:f0420000-f043ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 4
       logical name: ra0
       serial: 00:24:01:14:68:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.0 ip=192.168.1.4 multicast=yes wireless=Ralink STA

```

**7 ) Scan for networks (eth1)**
```

eth1      Interface doesn't support scanning.

```

**8 ) Ubuntu Version: **
```
Description:    Ubuntu 10.04.1 LTS

```

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
```
2.6.32-24-generic x86_64

```

**10 ) Restarting the network (ra0 is my USB device)**
```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface ra0=ra0.
                                                                         [ OK ]

```


I hope that you have enough informations to help me ! Otherwise, just tell me what I have to give you (with the command line please, I'm a beginner).


Thanks !

---

### Post by Sealbhach on 2010-08-25
I'm having trouble with wireless myself, with a different network card. I don't know what the problem is.

As a workaround, try installing wicd and connect with that. You can find wicd in Synaptic Package Manager. That works for me, will probably work for you too.

.

---

### Post by Wallion on 2010-08-25
I already tried it, it doesn't work.

---

### Post by Sealbhach on 2010-08-25
Ok. Well, why not try loading up the Live version again, run lsmod, and find out of there's a module that's not loading when you boot from the hard drive. 

Also, run 

```
sudo /etc/init.d/networking restart
```

to see if that gives you any information.

.

---

### Post by JBAlaska on 2010-08-25
To the OP, are you using a ralink plugin USB wireless adapter as well as the Broadcom wireless that's in your laptop? If so unplug it before doing the following:

To get the internal Broadcom wireless working:
Put the Ubuntu LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below **"Installable from CDROM"**. Then open a terminal and do:

```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the **Broadcom STA** driver in **System, Administration, Hardware Drivers**

You may need to reboot again to enable the driver.

---

### Post by Wallion on 2010-08-26
I still have the problem. And I have a new one : When I reboot my laptop, my USB device for the WIFI is not recognized anymore.

To be sure, I will format all my HD (Dell and Win7's partitions too) and check if my card will "work" again. It's not my first problem on Ubuntu with the Dell's partition (and the problem was at each reboot).

I'll give you news tonight !

---

### Post by Wallion on 2010-08-26
Okay... I haven't format yet, but it works ! I think that what you told me, JBAlaska, is working ! I tried different sessions, many reboots and it's always working !

So I apologize and thanks you a lot !


Goodbye.

---

