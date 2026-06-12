---
title: "broadcom-Not detecting any wireless networks-"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by paimpalil on 2010-09-16
Hi all,
I am having **[COLOR=Black]*HP ZD8000 laptop(5 years old)*[B]. **[/COLOR][/B]1GB DDR2 SDRAM,Mobile Pentium 4 520 2.8GHz, with Hyper-Threading,Realtek RTL8193 10/100 Ethernet LAN,Broadcom 802.11b/g Wireless LAN. I installed ubuntu 10.04.1 LTS. ubuntu is installed alone.no windows or any other OS. It works nice  with wired network but it never detects wireless networks. I installed all linux drivers for broadcom given in sofware center/synaptic, ndiswrapper, wicd, also network manager. All failed in purpose. What to do next? please advice. Thanks..

---

### Post by grahammechanical on 2010-09-16
Please try the tests suggested in the Ubuntu Wireless Trouble Shooting guide [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) Collect the information because it will be useful to someone more experienced than myself to solve the problem if you do not solve it yourself.

Regards. ;)

---

### Post by paimpalil on 2010-09-16
Hi
I installed b43 driver, fwcutter,broadcom sta driver too but nothing works.and for the command [lsmod it comes out as]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lsmod")
laptop:~$  lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_oss            26726  0 
pcmcia                 33024  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                674824  3 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 radeon
drm_kms_helper         29297  1 radeon
video                  17375  0 
tifm_7xx1               3690  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162409  5 radeon,ttm,drm_kms_helper
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
output                  1871  1 video
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
intel_agp              24119  0 
tifm_core               6045  1 tifm_7xx1
lp                      7028  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               2864  1 sdhci
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
psmouse                63245  0 
serio_raw               3978  0 
i2c_algo_bit            5028  1 radeon
agpgart                31724  3 ttm,drm,intel_agp
parport                32635  2 ppdev,lp
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
ieee1394               81181  1 ohci1394
mii                     4381  2 8139too,8139cp


laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:8a:9e:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.23.100 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:5000(size=256) memory:c8209400-c82094ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
       resources: memory:c8206000-c8207fff


Any more suggestions? Thanks..

---

### Post by PRC09 on 2010-09-16
You have activated the driver I presume under System > Administration > Hardware Drivers..If not give that a try and reboot.....

---

### Post by paimpalil on 2010-09-24
hi
thats not working.. any other suggestions? thanks..

---

### Post by PRC09 on 2010-09-25
Not sure where to go from here.I have always set that wireless card up on a fresh install and never had any problems so my troubleshooting for your problem is limited.Plus everything you have installed and tried I dont know if there is a way to clear everything you have done thus far and start again,other than re-install the OS.....And if you do re-install connect to your modem/router and do the updates,then while connected check for the drivers under the System > Admin > Hardware Drivers and they should be there to activate.Sorry not much help but it should solve the problem......

---

### Post by paimpalil on 2010-09-28
hi
I reinstalled ubuntu. They prompted to install new driver b43 for broadcom. Did it.and installed updates as usual.  Then I installed wicd meta package. Then it said device not ready. Rebooted. It worked.. Thanks...

---

