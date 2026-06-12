---
title: "Wireless not recognized - Broadcom 4318, have tried installing b43-fwcutter"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by blackbelt22 on 2009-07-02
Hi, I just installed Ubuntu today and am having some trouble.  As per the suggestions, I will post the relevant information.

Dell Inspiron 6000 laptop

Broadcom BCM4318 [Airforce One 54g]

**Interface**:
wlan0     Link encap:Ethernet  HWaddr 00:16:ce:0e:ca:4b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**Modules**
Module                  Size  Used by
isofs                  39844  1 
rfkill_input           12800  0 
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18368  0 
snd_intel8x0           37532  3 
arc4                    9856  2 
ecb                    10752  2 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
b43                   131484  0 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
mac80211              217208  1 b43
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0 
cfg80211               38032  1 mac80211
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
psmouse                61972  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
yenta_socket           32396  1 
led_class              12036  1 b43
pcspkr                 10496  0 
serio_raw              13316  0 
intel_agp              34108  0 
dcdbas                 15264  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
rsrc_nonstatic         19328  1 yenta_socket
input_polldev          11912  1 b43
agpgart                42696  2 drm,intel_agp
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  25360  0 
output                 11008  1 video
b44                    35984  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
ssb                    41220  2 b43,b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

[B]Network configuration

[/B]       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ee:e2:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.5 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:0e:ca:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: e6:68:84:7d:48:72
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

**Scan for networks** 

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:82:4F:B0
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/100  Signal level:-75 dBm  Noise level=-73 dBm
                    Encryption key:off
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020105
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000012b2e46f18a
                    Extra: Last beacon: 76ms ago

[B]Ubuntu 9.04

Kernel[/B]
2.6.28-11-generic i686




I did some research earlier and I found that I might be missing a driver for broadcom called b43-fwcutter.  I found directions for how to build fwcutter at linuxwireless because i could not use sudo apt-get to install it.  However, even after building it, when everything seemed to go ok without error messages, it would not work even after restarting.

Help?

---

### Post by spd106 on 2009-07-04
First check that you have the *.fw firmware files in your /lib/firmware/b43 folder.

If so then can you please post the last few lines of the output from *dmesg*. Any lines that mention b43, broadcom or wlan0 would be useful.

---

