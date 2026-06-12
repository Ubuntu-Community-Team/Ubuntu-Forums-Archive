---
title: "Wireless will not connect, continually prompts for password"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by watsonly on 2010-09-11
Hello! 

I am a bare beginner. I had my wireless working with Karmic Koala, but then after the updates/randomly last night my wireless disconnected. Now it will connect at random moments for a brief period of time, but mostly it prompts me over and over again for the password to my home network (although it was previously entered and I am sure it is correct) and then will not connect. My ethernet IS working.

I am running an Inspiron E1505 (Dell), Broadcom BCM4311 (802.11b/g WLAN (rev 01)).

I've done router restarting, I'm not running ndiswrapper, I do think I'm running bcm43xx.

Below is crazy loads of information from Terminal: 
~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"(wireless network name)"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec_idt      51978  1 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
joydev                  8708  0 
arc4                    1153  2 
radeon                674824  3 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
ttm                    49943  1 radeon
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
drm_kms_helper         29297  1 radeon
b43                   163523  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm                   162409  5 radeon,ttm,drm_kms_helper
psmouse                63245  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit            5028  1 radeon
ricoh_mmc               2923  0 
sdhci_pci               5470  0 
intel_agp              24119  0 
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              205146  1 b43
soundcore               6620  1 snd
sdhci                  15462  1 sdhci_pci
dell_wmi                1793  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
cfg80211              126517  2 b43,mac80211
serio_raw               3978  0 
led_class               2864  2 b43,sdhci
lp                      7028  0 
video                  17375  0 
output                  1871  1 video
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
parport                32635  2 ppdev,lp
b44                    25574  0 
ohci1394               26950  0 
ssb                    38671  2 b43,b44
ieee1394               81181  1 ohci1394
mii                     4381  1 b44

$dmesg
[   67.808217] wlan0: deauthenticating from 00:25:9c:b4:aa:0a by local choice (reason=3)
[   67.816461] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 1)
[   68.016060] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 2)
[   68.220030] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 3)
[   68.416056] wlan0: direct probe to AP 00:25:9c:b4:aa:0a timed out
[   79.172224] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 1)
[   79.372064] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 2)
[   79.572070] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 3)
[   79.772074] wlan0: direct probe to AP 00:25:9c:b4:aa:0a timed out
[   90.492243] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 1)
[   90.692055] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 2)
[   90.892053] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 3)
[   91.092061] wlan0: direct probe to AP 00:25:9c:b4:aa:0a timed out
[  101.817220] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 1)
[  102.016107] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 2)
[  102.219133] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 3)
[  102.416058] wlan0: direct probe to AP 00:25:9c:b4:aa:0a timed out
[  113.164232] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 1)
[  113.364085] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 2)
[  113.564078] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 3)
[  113.764072] wlan0: direct probe to AP 00:25:9c:b4:aa:0a timed out
[  124.532221] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 1)
[  124.732068] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 2)
[  124.932066] wlan0: direct probe to AP 00:25:9c:b4:aa:0a (try 3)
[  125.136069] wlan0: direct probe to AP 00:25:9c:b4:aa:0a timed out

~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efcfc000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:06:fb:f6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.107 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:45:49:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

network scan, this is the one I want to be able to connect to: 
Cell 02 - Address: 00:25:9C:B4:AA:0A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"(network name)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002ee6419f
                    Extra: Last beacon: 3340ms ago
                    IE: Unknown: 000863656D686F6D6565
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100000259CB4AA0A102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304A4141363437301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000

~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS

~$uname -mr
2.6.32-24-generic i686

Please, please, please help me or tell me if you need any further information.

---

### Post by Cloud_704 on 2010-09-12
*... wireless disconnected. Now it will connect at random moments for a brief period of time, but mostly it prompts me over and over again for the password to my home network (although it was previously entered and I am sure it is correct) and then will not connect. My ethernet IS working.*

I have basically same problem in 10.04. I can get on the wireless network, but, apparently at random, I will get kicked off, anywhere from less than a minute to about 15 minutes after connection was established (and the intervals seem to be getting shorter!) During the disconnected time the password prompt window pops up over and over. The time to successfully reestablish also seems random.

---

