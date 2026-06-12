---
title: "No Wifi on Acer Travelmate with Intel Pro/Wireless 2200BG on new ubuntu 10.10 install"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by Jeremai on 2011-01-17
Hello everyone willing to help me... I have an Acer Travelmate 4002LMI which I just stripped of Windows. Last night I did a fresh install of  Ubuntu 10.10 32bit as sole OS. Not much to my surprise, the install finished adn I had no internet. It sees networks but will not connect at all. This is the main problem, although you should know that the ethernet doesnt work either so I have no internet connection. But the WIFI is more crucial. I've searched the forums and tried a few things but nothing seemed to work. I'm posting the output of a few hopefully useful commands.

output of **lshw -c network**
*-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:8f:4f:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:6 memory:d0204000-d0205fff memory:24000000-24003fff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:22:55:72
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:10 memory:d0208000-d0208fff



output of **lsmod**
Module                  Size  Used by
arc4                    1165  2 
lib80211_crypt_wep      2647  1 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8735  0 
radeon                825934  3 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  0 
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
ipw2200               136715  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
libipw                 39808  1 ipw2200
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168054  5 radeon,ttm,drm_kms_helper
rt2870sta             405890  0 
irda                  178938  0 
tifm_7xx1               3766  0 
cfg80211              144470  2 ipw2200,libipw
intel_agp              26360  1 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
tifm_core               6089  1 tifm_7xx1
video                  18712  0 
i2c_algo_bit            5168  1 radeon
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
output                  1883  1 video
crc_ccitt               1351  2 irda,rt2870sta
soundcore                880  1 snd
lib80211                5058  3 lib80211_crypt_wep,ipw2200,libipw
psmouse                59033  0 
agpgart                32011  3 ttm,drm,intel_agp
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
serio_raw               4022  0 
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
b44                    26253  0 
firewire_ohci          21106  0 
ssb                    39288  1 b44
firewire_core          46643  1 firewire_ohci
mii                     4425  1 b44
crc_itu_t               1383  1 firewire_core

output **sudo iwlist eth1 auth**
eth1      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		Unknown
          Current Key management :
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current Pairwise cipher :
		WEP-104
		Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : no
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : yes
          Current Privacy invoked : yes

If you can help me at all I would really appreciate it. Im not a complete noob but still need much help. Thank you

---

### Post by bilderbuchi on 2012-07-21
If you still encounter this problem, see [http://askubuntu.com/a/166331/11069](http://askubuntu.com/a/166331/11069). you probably got to install the acerhk module

---

### Post by NikTh on 2012-07-21
Hi , 
**Question:** Why you prefer and old and not supported Ubuntu version , from a new (ubuntu 12.04) , with advantages like : Newer Kernel , better hardware compatibility , newer packages ... etc ? 

Regards

---

### Post by bilderbuchi on 2012-07-22
What are you talking about? I'm on 12.04... which doesn't have the acerhk module any more, that's why you have to work around it a bit.

---

