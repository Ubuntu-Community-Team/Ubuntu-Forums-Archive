---
title: "Wireless problem"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by ulriksvensson on 2010-04-03
Hi all.

I've just installed kubuntu 9.10 (fresh) and everything is working perfectly exept my wireless connection. I've tried to get it working with ndiswrapper with no luck. I've searched on google for a week now with no luck either. Here are my details:

Kernel: 2.6.31-20-generic
Arch. x86_64 (the Windows-driver I've used for ndiswrapper is also 64-bit)

```
ulrik@ulrik:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: ssb)
```I've tried to blacklist ssb but it doesn't help. Also,

```
ulrik@ulrik:~$ sudo rmmod ssb
ERROR: Module ssb does not exist in /proc/modules
``````
ulrik@ulrik:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
ulrik@ulrik:~$ lshw -C Network                     
WARNING: you should run this program as super-user.
  *-network:0                                      
       description: Ethernet interface             
       product: RTL-8169 Gigabit Ethernet          
       vendor: Realtek Semiconductor Co., Ltd.     
       physical id: 9                              
       bus info: pci@0000:00:09.0                  
       logical name: eth0                          
       version: 10                                 
       serial: 00:03:0d:38:c6:37                   
       width: 32 bits                              
       clock: 66MHz                                
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.34 latency=64 maxlatency=64 mingnt=32 multicast=yes                                                                                                                                        
       resources: irq:17 ioport:e800(size=256) memory:febff400-febff4ff memory:febc0000-febdffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wlan0
       version: 02
       serial: 00:14:a5:40:d9:ab
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.56+Broadcom,03/23/2006, 4.40.1 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:febfc000-febfdfff
```Finally,

```
ulrik@ulrik:~$ iwlist wlan0 scan
wlan0     No scan results
```I've never had an issue with wireless in Ubuntu (or even Ubuntu 9.10 before the last fresh install) except for slow connection, which is probably due to poorly working driver. I dual boot with Fedora 12 and (when I can boot this, which is another issue that belongs to some other forum) have no trouble with wireless there without using ndiswrapper.

Please let me know if I need to post more info.

//Ulrik

---

### Post by duanedesign on 2010-04-03
i read the driver is not included in the 9.10(Karmic) live cd or that there is a bug on the 9.10(Karmic)live cd. So on a fresh Karmic install you need to run update manager to get the appropriate driver. (hopefully you have an ethernet connection)

```
System -> Administration -> Update Manager
```

The BCM4318 chipset uses B43 driver

```
System -> Administration -> Hardware Drivers
```


Additional Resources:

[https://help.ubuntu.com/community/Wi...Driver/bcm43xx](https://help.ubuntu.com/community/Wi...Driver/bcm43xx)

---

### Post by ulriksvensson on 2010-04-03
Nope, this isn't the problem since I've even done a kernel update since the fresh install. It didn't show up in hardware drivers. I'll have a look at the link you posted.

---

### Post by ulriksvensson on 2010-04-03
The link gave me no help either. The problem persists.

---

### Post by coffeeaddict22 on 2010-04-04
Hi,
What's the output of ```
lsmod
```
And iwlist scan (the first command you posted) won't output anything without root priveleges- run it again with sudo.

On the stuff you've posted, you've got a working wireless.  Are you trying to set up a connection with Network Manager?   What happens when you do?

---

### Post by ulriksvensson on 2010-04-04
Hi.

Here's the output of lsmod and sudo iwlist wlan0 scan:

```
ulrik@ulrik:~$ lsmod
Module                  Size  Used by
binfmt_misc            10220  1      
ppdev                   8232  0      
joydev                 13088  0      
iptable_filter          3872  0      
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables     
amd64_edac_mod         26688  0               
snd_via82xx            28364  1               
gameport               13712  1 snd_via82xx   
snd_via82xx_modem      13804  6               
snd_ac97_codec        125720  2 snd_via82xx,snd_via82xx_modem
ac97_bus                2176  1 snd_ac97_codec               
lp                     11908  0                              
ndiswrapper           243456  0                              
psmouse                57124  0                              
serio_raw               6596  0                              
edac_core              48876  1 amd64_edac_mod               
snd_pcm_oss            44704  0                              
snd_mixer_oss          18976  1 snd_pcm_oss                  
snd_pcm                93160  6 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart         8480  1 snd_via82xx                                             
i2c_viapro              8696  0                                                         
snd_seq_dummy           3460  0                                                         
shpchp                 37756  0                                                         
parport                40528  2 ppdev,lp                                                
k8temp                  5504  0                                                         
snd_seq_oss            33440  0                                                         
snd_seq_midi            8192  0                                                         
snd_rawmidi            27296  2 snd_mpu401_uart,snd_seq_midi                            
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi                                
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  24 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  3 snd_via82xx,snd_via82xx_modem,snd_pcm
radeon                684576  2
ttm                    43056  1 radeon
drm                   194400  4 radeon,ttm
video                  23612  0
ohci1394               33780  0
i2c_algo_bit            7076  1 radeon
output                  3680  1 video
ieee1394              100896  1 ohci1394
r8169                  38884  0
mii                     6368  1 r8169
sata_via               12132  0
```

and

```
ulrik@ulrik:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

I've tried to configure wlan0 with knetworkmanager (which worked fine before). The interface shows up (wlan0) but also with this I get no scan results.

---

### Post by ulriksvensson on 2010-04-04
Here's a screen dump from knetworkmanager

---

### Post by coffeeaddict22 on 2010-04-04
I'm not familiar with knetworkmanager.
You've got a working wireless on this; check what you've put into knetworkmanager as your network settings, as that's probably where your problem lies.

---

### Post by ulriksvensson on 2010-04-05
Even if there's something wrong in the settings in knetworkmanager (which I think not) I should still be able to do sudo iwlist wlan0 scan if the device was working.

---

### Post by ulriksvensson on 2010-04-07
After doing another fresh reinstall of Kubuntu 9.10 I ran lshw -C Network as soon as I'd done all the updates. It said that the wireless card is DISABLED. The button for the WLAN on my laptop is switched on and the lamp for the wlan is indicating that it is turned on.
 
Even if the native drivers in Ubuntu workes very bad for my card, wy on earth does it get switched off? Is there some new setting in grub that turnes it off on boot? Anyway this has to be the core of my problem. If anyone knows anything about this I'd appreciate it.
 
//Ulrik

---

### Post by ulriksvensson on 2010-04-07
Solved this by installing b43-fwcutter. Then configured wifi with knetworkmanager. 10-4

---

### Post by bellyoffire on 2010-04-09
Thank you for this. It was so simple to just install both and then the wireless light started working and the wireless card started working.  I tried some other methods and they didnt work. One of them messed up the OS install so I had to do a fresh install myself.

---

### Post by ulriksvensson on 2010-04-18
Ok. I did the horrible mistake to upgrade to kde 4.4. Now the wireless doesn't work again. Looking forward to another fresh install...

---

