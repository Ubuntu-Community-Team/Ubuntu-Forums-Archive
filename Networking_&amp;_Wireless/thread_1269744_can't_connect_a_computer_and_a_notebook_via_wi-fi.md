---
title: "can't connect a computer and a notebook via wi-fi"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by netimen on 2009-09-18
I have an **Acer Timeline 4810G** notebook and a desktop computer. I bought a **D-Link DWA-110** USB Wi-Fi adapter and tried to connect both systems via Wi-Fi.
I have **Kubuntu 9.04** on my desktop and **Ubuntu 9.04** on my notebook.
I created new wireless network on my notebook (without any security) and tried to connect to it from my desktop. But though my desktop saw that network (it appeared in **knetworkmanager**) it can't connect to it. When I press 'connect' it tries to connect, but after several moments of trying it stays disconnected.

Here is some information for the desktop (I'm not sure I should post all of this for the notebook because I know wi-fi works OK on it: I successefully connected to some networks):

lsusb output:
```
Bus 001 Device 002: ID 07d1:3c07 D-Link System Wireless G DWA-110 Adapter
```

this is my kernel version on desktop: 2.6.28-11-generic

this is my lsmod output:
```
Module                  Size  Used by                                                                                                                                                        
arc4                    9856  2                                                                                                                                                              
ecb                    10752  2                                                                                                                                                              
rt73usb                33412  0                                                                                                                                                              
crc_itu_t              10112  1 rt73usb                                                                                                                                                      
rt2x00usb              18688  1 rt73usb                                                                                                                                                      
rt2x00lib              37888  2 rt73usb,rt2x00usb                                                                                                                                            
led_class              12036  1 rt2x00lib                                                                                                                                                    
mac80211              217208  2 rt2x00usb,rt2x00lib                                                                                                                                          
cfg80211               38032  2 rt2x00lib,mac80211                                                                                                                                           
binfmt_misc            16776  1                                                                                                                                                              
bridge                 56340  0                                                                                                                                                              
stp                    10500  1 bridge                                                                                                                                                       
bnep                   20224  2                                                                                                                                                              
input_polldev          11912  0                                                                                                                                                              
video                  25360  0                                                                                                                                                              
output                 11008  1 video                                                                                                                                                        
vfat                   18816  0                                                                                                                                                              
fat                    58272  1 vfat                                                                                                                                                         
dm_crypt               20996  0                                                                                                                                                              
lp                     17156  0                                                                                                                                                              
snd_ca0106             39968  2
snd_ac97_codec        112292  1 snd_ca0106
snd_pcm_oss            46336  0
snd_mixer_oss          22656  2 snd_pcm_oss
iptable_nat            13700  0
snd_pcm                82948  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
iptable_mangle         10880  0
snd_seq_midi           14336  0
iptable_filter         10752  0
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
snd_rawmidi            29696  2 snd_ca0106,snd_seq_midi
x_tables               23044  2 iptable_nat,ip_tables
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  15620  0
psmouse                61972  0
snd                    62628  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  2 snd
k8temp                 12416  0
pcspkr                 10496  0
serio_raw              13316  0
ac97_bus                9856  1 snd_ac97_codec
snd_page_alloc         16904  2 snd_ca0106,snd_pcm
nvidia               7233756  36
i2c_nforce2            14980  0
agpgart                42696  1 nvidia
parport_pc             40100  1
parport                42220  3 lp,ppdev,parport_pc
forcedeth              61712  0
floppy                 64324  0
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```

dmesg | grep firmware output:
```
[ 1948.676341] rt73usb 1-7:1.0: firmware: requesting rt73.bin

```

dmesg | grep wlan output:
```
[ 1948.921616] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1950.514881] wlan0: authenticate with AP 00:23:f8:86:52:94
[ 1950.712177] wlan0: authenticate with AP 00:23:f8:86:52:94
[ 1950.912282] wlan0: authenticate with AP 00:23:f8:86:52:94
[ 1951.112031] wlan0: authentication with AP 00:23:f8:86:52:94 timed out
[ 2147.953423] wlan0: direct probe to AP 00:23:f8:86:52:94 try 1
[ 2147.960587] wlan0 direct probe responded
[ 2147.960595] wlan0: authenticate with AP 00:23:f8:86:52:94
[ 2148.166731] wlan0: authenticate with AP 00:23:f8:86:52:94
[ 2148.364036] wlan0: authenticate with AP 00:23:f8:86:52:94
[ 2148.564052] wlan0: authentication with AP 00:23:f8:86:52:94 timed out
[ 2389.757244] wlan0: direct probe to AP 00:23:f8:86:52:94 try 1
[ 2389.958218] wlan0: direct probe to AP 00:23:f8:86:52:94 try 2
[ 2390.174190] wlan0: direct probe to AP 00:23:f8:86:52:94 try 3
[ 2390.373053] wlan0: direct probe to AP 00:23:f8:86:52:94 timed out
[ 3334.195428] wlan0: direct probe to AP 00:23:f8:86:52:94 try 1
[ 3334.392052] wlan0: direct probe to AP 00:23:f8:86:52:94 try 2
[ 3334.592050] wlan0: direct probe to AP 00:23:f8:86:52:94 try 3
[ 3334.792031] wlan0: direct probe to AP 00:23:f8:86:52:94 timed out
```

---

### Post by netimen on 2009-09-20
I understood I have a bit different problem, so I devoted it a new post.

---

