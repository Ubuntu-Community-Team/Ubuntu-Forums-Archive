---
title: "Wireless &quot;device not ready&quot; on Natty with Intel 1000 wireless"
date: 2011-07-07
forum: Networking &amp; Wireless
---

### Post by pebuha on 2011-07-07
Hi everyone,

I'm running Linux 11.04 and my wireless network was working just fine until today. I cannot connect to WiFi - it acts as if the device wasn't there. The hardware switch led isn't working. No matter how much clicking on it, it won't work. 

iwconfig: 
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth1      no wireless extensions.

sudo lshw -C network  claims
> 
petar@petar-NB:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:38:af:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-10-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:49 memory:c4800000-c4801fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:26:9e:97:42:79
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5764m-v3.34 ip=192.168.0.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:46 memory:c4c00000-c4c0ffff
  *-network
       description: Ethernet interface
       physical id: 3
       bus info: usb@1:3
       logical name: eth1
       serial: fa:1e:df:57:b2:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes

lsmod  says
> 
Module                  Size  Used by
sparse_keymap          13898  0 
ipheth                 13478  0 
snd_hrtimer            12784  1 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
arc4                   12529  2 
joydev                 17606  0 
iwlagn                333717  0 
iwlcore               167503  1 iwlagn
mac80211              294370  2 iwlagn,iwlcore
rfcomm                 47694  12 
pcmcia                 49166  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
snd_hda_intel          33211  4 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  3 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
snd_timer              29602  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms              17596  0 
cfg80211              178528  3 iwlagn,iwlcore,mac80211
fglrx                2739144  110 
yenta_socket           27846  0 
pcmcia_rsrc            18372  1 yenta_socket
btusb                  18600  2 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
pcmcia_core            22569  3 pcmcia,yenta_socket,pcmcia_rsrc
memstick               16520  1 jmb38x_ms
snd                    67382  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw              13166  0 
soundcore              12680  1 snd
video                  19438  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
tg3                   141750  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
ahci                   25951  2 
libahci                26642  1 ahci



Additional info, help? Thanks!!! 

PS: Laptop - Acer Extensa 7630G, and internet using Ethernet cable works no problem.

PS2: some packages were updated yesterday, does it have anything to do with it?

---

### Post by wgarciamachmar on 2011-08-11
I have the exact same problem on a sony vaio.

---

### Post by chili555 on 2011-08-11
> **wgarciamachmar said:**
> I have the exact same problem on a sony vaio.Please run and post:```
rfkill list all
```Thanks.

---

### Post by wgarciamachmar on 2011-08-11
Hey! Solved the problem myself. It seems to be a "popular problem". I used the commands posted here [http://ubuntuforums.org/showthread.php?p=11141623#post11141623](http://ubuntuforums.org/showthread.php?p=11141623#post11141623)

---

