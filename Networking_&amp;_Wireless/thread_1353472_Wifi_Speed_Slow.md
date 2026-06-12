---
title: "Wifi Speed Slow"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by becho on 2009-12-12
I have been using Kubuntu for some time now and recently noticed my wifi has slowed down significantly. My ISP is Comcast and i am on the 8000/2000 plan with Powerboost. At various speed sites i am capped @ 8000/876. I did some research and i believe it to be a Kubuntu/Ubuntu bug. My wifi is capped @ 1Mbit bit-rate when I hover over the wifi icon. When I enter this code in terminal all my speed is brought back to normal 23000/4000 with Powerboost.

```
sudo iwconfig wlan0 rate 54M

``` 

Problem is that it is lost after a reboot and reverts back to 1Mbit Bit-rate for wlan0. How and where can I put the code so it sticks after a reboot. I was thinking it should go into /etc/network/interfaces but I don't the format how it should be entered. I tried entering this into interfaces 

```
iface wlan0 rate 54M
```

but the wlan0 loses connectivity. Here is more info:

```
auto lo
iface lo inet loopback
```

```
wlan0     IEEE 802.11bg  ESSID:"Virus Infected"
          Mode:Managed  Frequency:2.462 GHz  Access Point: **:**:**:**:**:**
          Bit Rate=1 Mb/s   Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/100  Signal level=44/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
Bus 004 Device 002: ID 1532:000c Razer USA, Ltd
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 045e:00b0 Microsoft Corp. Digital Media Pro Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
Module                  Size  Used by
cryptd                  8008  0      
aes_x86_64              8992  2      
aes_generic            28480  1 aes_x86_64
arc4                    2144  2           
ecb                     3296  2           
snd_hda_codec_atihdmi     4320  1         
zd1211rw               52520  0           
mac80211              209912  1 zd1211rw  
snd_hda_intel          31880  1           
snd_hda_codec          87584  2 snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec                      
snd_seq_dummy           3460  0                                    
snd_seq_oss            33440  0                                    
iptable_filter          3872  0                                    
ip_tables              21200  1 iptable_filter                     
x_tables               25832  1 ip_tables                          
snd_ctxfi              99016  2
snd_seq_midi            8192  0
snd_pcm_oss            44704  0
snd_mixer_oss          18976  1 snd_pcm_oss
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 13088  0
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                57124  0
ppdev                   8232  0
serio_raw               6596  0
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_ctxfi,snd_pcm_oss
snd_timer              26992  2 snd_seq,snd_pcm
parport_pc             37352  1
lp                     11908  0
parport                40528  3 ppdev,parport_pc,lp
snd                    77096  18 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq_oss,snd_ctxfi,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
cfg80211              109144  2 zd1211rw,mac80211
usbhid                 43968  0
radeon                684512  1
ttm                    43056  1 radeon
drm                   193856  3 radeon,ttm
i2c_algo_bit            7076  1 radeon
r8169                  38884  0
mii                     6368  1 r8169
floppy                 65192  0
intel_agp              32816  0

```

---

