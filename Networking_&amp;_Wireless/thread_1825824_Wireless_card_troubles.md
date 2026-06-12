---
title: "Wireless card troubles"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by electrojustin on 2011-08-15
Hello everyone, I am having wireless problems in ubuntu and have tried just about everything. When I try to connect to my network, it just shows the trying to connect animation indefinitely. Ive tried reloading the driver, using a windows driver with ndiswrapper, custom building the driver as a module, reloading the operating system, and reloading the operating system with ubuntu 10.04 LTS. I am using ubuntu 11.04 and my wireless card is of the rt2860sta chipset. I think its my card that went bad, but I'd like a second opinion before I buy a new one.

---

### Post by nm_geo on 2011-08-15
Let's see the following commands results;

```
lspci -nn | grep 0280
``````
modinfo rt2860sta 
``````
lsmod
``````
sudo lshw -C network
```Those should gives us a good start.

---

### Post by electrojustin on 2011-08-16
Ok. I will try those commands when I get home from vacation. Unfortunately no internet means no ssh so I cant try the commands right now :(. Thanks for the suggestion!

---

### Post by electrojustin on 2011-08-24
Back from vacation
lspci -nn | grep 0280:
```
justin@justin-desktop:~$ lspci -nn | grep 0280
03:06.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]

```
 
modinfo rt2860sta:
 
```
justin@justin-desktop:~$ modinfo rt2860sta
filename:       /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        1.8.1.1
license:        GPL
srcversion:     CAEA506C88572D233F96224
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
staging:        Y
vermagic:       2.6.32-21-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)][/
```
 
lsmod:
 
```
justin@justin-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
snd_hda_codec_atihdmi     3023  1 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_codec_realtek   278890  1 
snd_usb_audio          92747  1 
snd_usb_lib            18978  1 snd_usb_audio
snd_pcm_oss            41394  0 
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  2 snd_usb_audio,snd_hda_codec
joydev                 11072  0 
snd_pcm                87850  4 snd_usb_audio,snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                739595  3 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62403  0 
videodev               40486  1 uvcvideo
ttm                    60815  1 radeon
drm_kms_helper         30742  1 radeon
v4l1_compat            15495  2 uvcvideo,videodev
rt2860sta             542482  1 
v4l2_compat_ioctl32    12020  1 videodev
snd                    70978  19 snd_hda_codec_realtek,snd_usb_audio,snd_pcm_oss,snd_hda_intel,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   6375  0 
drm                   198770  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
edac_core              45423  0 
serio_raw               4918  0 
edac_mce_amd            9214  0 
usbhid                 40988  0 
keyspan                36404  0 
usbserial              39067  1 keyspan
hid                    83376  1 usbhid
i2c_piix4               9639  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
parport_pc             29958  1 
shpchp                 33679  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
ohci1394               30260  0 
floppy                 63156  0 
ieee1394               94675  1 ohci1394
r8169                  39554  0 
mii                     5237  1 r8169
pata_atiixp             4209  0 
ahci                   37646  3 
```
 
sudo lshw -C network:
 
```
justin@justin-desktop:~$ sudo lshw -C network
[sudo] password for justin: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 6c:f0:49:04:36:01
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdae0000-fdaeffff(prefetchable) memory:fda00000-fda0ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 00
       serial: 00:25:9c:e5:63:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:20 memo
```

---

### Post by electrojustin on 2011-08-26
bunp

---

### Post by praseodym on 2011-08-26
You can update the driver with the backports-modules, but you should first update your system, with Lucid kernel 2.6.32-33 is the newest one.

---

### Post by electrojustin on 2011-08-28
Ok I fixed it. Something in my home directory went screwy so I had to back up the data I cared about and reformat both the root partition and the /home partition :\.

---

