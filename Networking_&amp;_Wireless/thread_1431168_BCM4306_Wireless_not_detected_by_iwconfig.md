---
title: "BCM4306 Wireless not detected by iwconfig"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by johanpretorius on 2010-03-16
[COLOR=Blue]The PC's lspci[/COLOR]

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
**00:0b.0 Ethernet controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

[COLOR=Blue]lsmod:[/COLOR]
Module                  Size  Used by                                                                    
iptable_filter         10752  0                                                                          
ip_tables              19600  1 iptable_filter                                                           
x_tables               23044  1 ip_tables                                                                
b43                   131484  0                                                                          
mac80211              217592  1 b43
cfg80211               38288  1 mac80211
led_class              12036  1 b43
input_polldev          11912  1 b43
ssb                    41220  1 b43
wl                   1281364  0
ieee80211_crypt_tkip    16896  0
ieee80211_crypt        13444  2 wl,ieee80211_crypt_tkip
binfmt_misc            16776  1
video                  25872  0
output                 11008  1 video
lp                     17156  0
snd_intel8x0           37532  2
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
nvidia               7097928  34
ppdev                  15620  0
pcspkr                 10496  0
shpchp                 40212  0
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
sis_agp                15360  1
agpgart                42696  2 nvidia,sis_agp
parport_pc             40100  1
parport                42220  3 lp,ppdev,parport_pc
usb_storage            99648  0
usbhid                 42336  0
sis900                 28288  0
mii                    13312  1 sis900
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

[COLOR=Blue]lswh -C network[/COLOR]

  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth1
       version: 91
       serial: 00:14:2a:d1:f5:48
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=10.0.0.8 latency=32 link=yes maxlatency=11mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Ethernet controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb

[COLOR=Blue]iwconfig[/COLOR]:
lo        no wireless extensions.

eth1      no wireless extensions.

As you can see, the cards is recognised, modules is loaded but I cannot use it.
The lshw command shows it does not have a LOGICAL NAME.

Howto fix problem , please ?

---

### Post by p110011 on 2010-03-16
Are you using Karmic-9.10? I have that card in my HP ZV5000, works with fwcutter

---

### Post by johanpretorius on 2010-03-16
Kubuntu 9.3 cannot upgrade right now. Don't have the gig cap to do so now.

---

### Post by leorolla on 2010-03-16
It could be this "wl" module.

Try uninstalling bcmwl-kernel-source, blacklisting it, rebooting, and see if it still appears at lsmod.

And please, use the "code" tag when you copy-paste the output. It is this "#" that you see in the formatting toolbar, otherwise put [ code ] before and [ /code ] after (without spaces).

---

### Post by p110011 on 2010-03-16
Now that you pointed that out I see it. I also had made the mistake of loading that bcmwl-kernel-source from the live disk.

---

### Post by johanpretorius on 2010-03-16
I blacklisted wl module.
I did not have bcmwl-kernel-source installed or even in Synaptic.

This is how lsmod looks now:
```

Module                  Size  Used by                     
binfmt_misc            16776  1                           
video                  25872  0                           
output                 11008  1 video
lp                     17156  0
snd_intel8x0           37532  2
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   131484  0
nvidia               7097928  34
mac80211              217592  1 b43
snd                    62756  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gspca_spca561          18944  0
gspca_main             29952  1 gspca_spca561
ppdev                  15620  0
soundcore              15200  1 snd
videodev               41600  1 gspca_main
parport_pc             40100  1
cfg80211               38288  1 mac80211
sis_agp                15360  1
agpgart                42696  2 nvidia,sis_agp
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
shpchp                 40212  0
v4l1_compat            21764  1 videodev
parport                42220  3 lp,ppdev,parport_pc
pcspkr                 10496  0
led_class              12036  1 b43
input_polldev          11912  1 b43
usb_storage            99648  0
usbhid                 42336  0
ssb                    41220  1 b43
sis900                 28288  0
mii                    13312  1 sis900
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


```

Still nothing in iwconfig.

Thanks for your efforts so far.

---

### Post by p110011 on 2010-03-16
Is led_class a radio button? Off/on wireless? Mine is not working right with 9.10 and every other boot-up my wireless is hard-off.

---

