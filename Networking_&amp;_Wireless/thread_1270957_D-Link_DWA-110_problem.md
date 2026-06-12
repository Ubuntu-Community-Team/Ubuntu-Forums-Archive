---
title: "D-Link DWA-110 problem"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by netimen on 2009-09-20
I'm running **kubuntu 9.04** with **2.6.28-11-generic** kernel. I installed **D-Link DWA-110** usb Wi-Fi adapter. I see some wireless networks in **wicd**, but it fails to connect to them.

After several failed attempts I installed a driver via **ndiswrapper**, but that didn't help.

I installed my adapter into a Windows XP machine and successfully connected to a network.

Here is some useful info:

*lsusb* output:
```
Bus 001 Device 002: ID 07d1:3c07 D-Link System Wireless G DWA-110 Adapter
```

*lsmod* output:
```
Module                  Size  Used by                                    
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
arc4                    9856  2                                          
ecb                    10752  2                                          
snd_ca0106             39968  2                                          
snd_ac97_codec        112292  1 snd_ca0106                               
iptable_nat            13700  0                                          
nf_nat                 25876  1 iptable_nat                              
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat                       
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4     
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4                        
snd_pcm_oss            46336  0
snd_mixer_oss          22656  2 snd_pcm_oss
snd_pcm                82948  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
iptable_mangle         10880  0
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
iptable_filter         10752  0
snd_rawmidi            29696  2 snd_ca0106,snd_seq_midi
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
rt73usb                33412  0
crc_itu_t              10112  1 rt73usb
x_tables               23044  2 iptable_nat,ip_tables
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00usb              18688  1 rt73usb
rt2x00lib              37888  2 rt73usb,rt2x00usb
led_class              12036  1 rt2x00lib
mac80211              217208  2 rt2x00usb,rt2x00lib
ppdev                  15620  0
psmouse                61972  0
snd                    62628  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  2 snd
k8temp                 12416  0
pcspkr                 10496  0
serio_raw              13316  0
ac97_bus                9856  1 snd_ac97_codec
snd_page_alloc         16904  2 snd_ca0106,snd_pcm
cfg80211               38032  2 rt2x00lib,mac80211
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

*dmesg | grep firmware* output:
```
[   27.169834] rt73usb 1-7:1.0: firmware: requesting rt73.bin
```

*dmesg | grep wlan* output:
```
[   27.455744] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  823.632858] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2495.289497] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

*ndiswrapper -l* output:
```
dr71wu : driver installed
        device (07D1:3C07) present (alternate driver: rt73usb)
```

---

### Post by chili555 on 2009-09-20
> (alternate driver: rt73usb)This generally means that two drivers are fighting for world domination of your card; your *dmesg* entry seems to confirm it. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
rt73usb
```Proofread, save and close gedit. Reboot and see if things are improved.

---

### Post by netimen on 2009-09-20
Thank you for your answer!

I added line:
```
blacklist rt73usb
```

but *ndiswrapper -l* still gives:
```
dr71wu : driver installed
        device (07D1:3C07) present (alternate driver: rt73usb)

```

And now I don't even see the wireless networks in **wicd**

---

### Post by chili555 on 2009-09-21
Let's take a look at what modules are loading, and whether ndiswrapper is loading. Please post:```
lsmod
```Thanks.

---

### Post by netimen on 2009-09-21
lsmod:
```
Module                  Size  Used by
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
iptable_nat            13700  0       
snd_ac97_codec        112292  1 snd_ca0106
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4                   
snd_pcm_oss            46336  0                                     
snd_mixer_oss          22656  2 snd_pcm_oss                         
iptable_mangle         10880  0                                     
snd_pcm                82948  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0                                      
snd_seq_oss            37760  0                                      
snd_seq_midi           14336  0                                      
snd_rawmidi            29696  2 snd_ca0106,snd_seq_midi              
iptable_filter         10752  0                                      
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi                 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq                                          
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               23044  2 iptable_nat,ip_tables
psmouse                61972  0
snd                    62628  12 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  2 snd
ppdev                  15620  0
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

---

### Post by netimen on 2009-09-29
Yeah, I managed to solve this. The problem was that wicd couldn't connect to a network. But I managed to connect via console commands after settings the correct parameters (essid, ip etc) manually

---

