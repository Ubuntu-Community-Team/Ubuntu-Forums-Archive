---
title: "Toshiba NB550D Netbook running Ubuntu 11.04"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by m0n4g3 on 2011-07-13
Hi Guys

I've installed Ubuntu 11.04 on the above netbook and all is going well except for a few items.

I've had a few issues with the bluetooth adapter not being detected.

The card is a combo card with the following device code on it.

ath-ar5b195

This suggests that it's a AR9285 wireless chipset with a AR3011 bluetooth chipset packaged into one.

Unfortunately ubuntu doesn't detect it and am unable to use the bluetooth to connect my phone to the netbook and use it as a 3g modem.

I have tried xubuntu and it is detected in that but would prefer to use Ubuntu.

Any help on this front would be great!

I've run lspci and lsusb and it does not appear in there, but the ar9285 appears in lspci, but not the ar3011.

Thanks

---

### Post by m0n4g3 on 2011-07-14
Bump.

Any1 not able to help? :(

---

### Post by nm_geo on 2011-07-14
> **m0n4g3 said:**
> Bump.

Any1 not able to help? :(

Give us the results of 

```
lspci -nn | grep 0280
``````
sudo lshw -C network

``````
lsmod
```

---

### Post by m0n4g3 on 2011-07-15
Code:
     lspci -nn | grep 0280 
     renders the following:

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

Code:
     sudo lshw -C network 
     renders the following:


  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:7a:76:76
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:fea04000-fea04fff memory:fea00000-fea03fff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:03:10:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A ip=192.168.2.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fe900000-fe90ffff

Code:     lsmod

renders the following:

Module                  Size  Used by
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  3 bnep
btusb                  18600  1 
bluetooth              72320  8 sco,bnep,l2cap,btusb
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
snd_hda_codec_realtek   336771  1 
arc4                   12529  2 
ath9k                 118238  0 
snd_hda_codec_hdmi     28167  1 
mac80211              294370  1 ath9k
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
joydev                 17606  0 
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k_common           13851  1 ath9k
snd_seq_midi           13324  0 
ath9k_hw              323077  2 ath9k,ath9k_common
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    23773  2 ath9k,ath9k_hw
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178528  3 ath9k,mac80211,ath
uvcvideo               72195  0 
sp5100_tco             13744  0 
snd_timer              29602  2 snd_pcm,snd_seq
videodev               82052  1 uvcvideo
psmouse                73535  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17078  1 videodev
k10temp                13119  0 
serio_raw              13166  0 
fglrx                2795835  132 
snd                    67382  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13898  0 
toshiba_bluetooth      12807  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0 

The wireless works fine, just not the bluetooth :-/

When using the bluetooth app it says bluetooth is disabled, when i click the turn on button it just greys out and nothing happens.

Also FWIW running jockey (both gui and cli) doesn't show up any hardware apart from the AMD video drivers (installed the ones from amd website anyway)

---

### Post by m0n4g3 on 2011-07-16
I did find this. Seems to be exactly what's happening as the Toshiba device in lsusb specifies the same ID

[http://www.spinics.net/lists/linux-bluetooth/msg14589.html](http://www.spinics.net/lists/linux-bluetooth/msg14589.html)

But no idea how to apply said patch/fix? :(

---

### Post by m0n4g3 on 2011-07-17
is any one able to help me out with this?

I'm trying my best to search with google and search the forums for help on this, but seems like it's too new a card/laptop to get any useful information.

I'm wanting to try the compat-wireless drivers from the linux wireless website but not 100% sure if it will kill my install or not... :-/

Any help would be muchly appreciated, and if you require any extra information i'm glad to give it to you.

Thanks
m0n

---

