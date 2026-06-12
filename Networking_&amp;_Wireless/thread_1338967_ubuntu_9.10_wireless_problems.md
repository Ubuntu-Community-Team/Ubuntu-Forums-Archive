---
title: "ubuntu 9.10 wireless problems"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by spriizha on 2009-11-27
Hello. Just installed Ubuntu 9.10. Everything looks like working, except the wireless of curse. O.K. - some details:
Laptop model:
```
HP compaq mx9105
```
lspci:
```
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```
lsmod:
```
Module                  Size  Used by
binfmt_misc             8356  1      
snd_intel8x0           30168  2      
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0               
snd_mixer_oss          16028  1 snd_pcm_oss   
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0                                        
snd_seq_oss            28576  0                                        
snd_seq_midi            6432  0                                        
snd_rawmidi            22208  1 snd_seq_midi                           
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi               
arc4                    1660  2                                        
iptable_filter          3100  0                                        
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ecb                     2524  2                                                          
ip_tables              11692  1 iptable_filter                                           
snd_timer              22276  2 snd_pcm,snd_seq                                          
pcmcia                 36808  0                                                          
bridge                 47952  0                                                          
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   122136  0                                                           
x_tables               16544  1 ip_tables                                                 
stp                     2272  1 bridge                                                    
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24200  2                                                                                                                        
mac80211              181236  1 b43                                                                                                                    
bnep                   12060  2                                                                                                                        
ppdev                   6688  0                                                                                                                        
soundcore               7264  1 snd                                                                                                                    
rsrc_nonstatic         11644  1 yenta_socket                                                                                                           
cfg80211               93052  2 b43,mac80211                                                                                                           
psmouse                56500  0                                                                                                                        
parport_pc             31940  1                                                                                                                        
led_class               4096  1 b43                                                                                                                    
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm                                                                                                   
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic                                                                                     
i2c_nforce2             6784  0                                                                                                                        
joydev                 10272  0                                                                                                                        
k8temp                  4188  0                                                                                                                        
btusb                  11856  2                                                                                                                        
shpchp                 32272  0                                                                                                                        
serio_raw               5280  0                                                                                                                        
lp                      8964  0                                                                                                                        
parport                35340  3 ppdev,parport_pc,lp                                                                                                    
usbhid                 38208  0                                                                                                                        
8139too                22620  0                                                                                                                        
ssb                    35300  1 b43                                                                                                                    
8139cp                 19260  0                                                                                                                        
mii                     5212  2 8139too,8139cp                                                                                                         
ohci1394               29900  0                                                                                                                        
ieee1394               86596  1 ohci1394                                                                                                               
video                  19380  0                                                                                                                        
output                  2780  1 video                                                                                                                  
amd64_agp               9796  1                                                                                                                        
agpgart                34988  1 amd64_agp                                                                                                              
luckymike@oldschool:~$ lsmod | grep "wlan_module_name"                                                                                                 
luckymike@oldschool:~$ lsmod | grep b43
b43                   122136  0 
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
ssb                    35300  1 b43
luckymike@oldschool:~$ lsmod       
Module                  Size  Used by
binfmt_misc             8356  1      
snd_intel8x0           30168  2      
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0               
snd_mixer_oss          16028  1 snd_pcm_oss   
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0                                        
snd_seq_oss            28576  0                                        
snd_seq_midi            6432  0                                        
snd_rawmidi            22208  1 snd_seq_midi                           
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi               
arc4                    1660  2                                        
iptable_filter          3100  0                                        
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ecb                     2524  2                                                          
ip_tables              11692  1 iptable_filter                                           
snd_timer              22276  2 snd_pcm,snd_seq                                          
pcmcia                 36808  0                                                          
bridge                 47952  0                                                          
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
b43                   122136  0                                                           
x_tables               16544  1 ip_tables                                                 
stp                     2272  1 bridge                                                    
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           24200  2                                                                                                                        
mac80211              181236  1 b43                                                                                                                    
bnep                   12060  2                                                                                                                        
ppdev                   6688  0                                                                                                                        
soundcore               7264  1 snd                                                                                                                    
rsrc_nonstatic         11644  1 yenta_socket                                                                                                           
cfg80211               93052  2 b43,mac80211                                                                                                           
psmouse                56500  0                                                                                                                        
parport_pc             31940  1                                                                                                                        
led_class               4096  1 b43                                                                                                                    
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm                                                                                                   
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic                                                                                     
i2c_nforce2             6784  0                                                                                                                        
joydev                 10272  0                                                                                                                        
k8temp                  4188  0                                                                                                                        
btusb                  11856  2                                                                                                                        
shpchp                 32272  0                                                                                                                        
serio_raw               5280  0                                                                                                                        
lp                      8964  0                                                                                                                        
parport                35340  3 ppdev,parport_pc,lp                                                                                                    
usbhid                 38208  0                                                                                                                        
8139too                22620  0
ssb                    35300  1 b43
8139cp                 19260  0
mii                     5212  2 8139too,8139cp
ohci1394               29900  0
ieee1394               86596  1 ohci1394
video                  19380  0
output                  2780  1 video
amd64_agp               9796  1
agpgart                34988  1 amd64_agp

```
dmesg | grep b43:

```
[    2.660946] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   16.529171] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   17.892085] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.299310] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   18.305378] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   18.305385] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   18.305389] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   21.262030] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   21.270809] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   21.280728] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   21.280735] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   21.280739] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   45.074932] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   45.092783] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   45.117891] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   45.117898] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   45.117902] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```
iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.

```

Actually i do not get what i do not get. :( but hope that someone could give me some hints to what to do. i tried to look the [httP://wireless.kernel.org](httP://wireless.kernel.org) but all that information is to dark for me. :(

// Sorry for long prints, but i do not know what info exactly should i print here :( //

[COLOR="Red"]SORRY for topic, i plugged laptop to cable and made update, after that in driver manager showed driver.[/COLOR] if you can, then delete or lock this.

---

### Post by bkratz on 2009-11-27
Ignore this! finally read the last line!


See post 4 in the following:

[http://ubuntuforums.org/showthread.php?t=1328969&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=1328969&highlight=BCM4306)

Good Luck

---

### Post by CoolDreamZ on 2009-11-28
This is a known issue in 9.10 (which you solved by making a wired connection and running an update). Many people are experiencing this problem, for example see here:

[http://ubuntuforums.org/showthread.php?t=1312603]("http://ubuntuforums.org/showthread.php?t=1312603")

---

