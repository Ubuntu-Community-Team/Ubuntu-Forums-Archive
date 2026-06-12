---
title: "Slow Wireless"
date: 2013-05-23
forum: Networking &amp; Wireless
---

### Post by stellar ashes on 2013-05-23
Hi,

I just upgraded from 11.10 to 12.04 and the wireless connection is incredibly slow and times out often. 
In 11.10 I had the same problem already earlier which was related to the N-channel support on the card.

In 11.10 I solved it by:
```

sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1

```
(Source: [http://ubuntuforums.org/showthread.php?p=11360822](http://ubuntuforums.org/showthread.php?p=11360822))

Now this does not work in 12.04 unfortunately. I am working on a Fujitsu Lifebook T5010.

Some output of my system:

sudo lshw -C network

```

  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:17:42:f8:0c:e9
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f2700000-f271ffff memory:f2725000-f2725fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:1c:99:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-43-generic-pae firmware=8.83.5.1 build 33692 ip=192.168.1.38 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f2500000-f2501fff
```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:17:42:f8:0c:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2700000-f2720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113124 (113.1 KB)  TX bytes:113124 (113.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:1c:99:e6  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44749 (44.7 KB)  TX bytes:364255 (364.2 KB)

```


iwconfig

```

eth0      Link encap:Ethernet  HWaddr 00:17:42:f8:0c:e9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2700000-f2720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113124 (113.1 KB)  TX bytes:113124 (113.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6a:1c:99:e6  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3669 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44749 (44.7 KB)  TX bytes:364255 (364.2 KB)

```

lsmod

```
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  12 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
usblp                  17885  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
arc4                   12473  2 
wacom_w8001            12906  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
pcmcia                 39826  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
serport                12808  1 
psmouse                86520  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
iwlwifi               366509  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mac80211              436493  1 iwlwifi
joydev                 17393  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i915                  423564  3 
btusb                  17948  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178877  2 iwlwifi,mac80211
bluetooth             158479  23 bnep,rfcomm,btusb
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
fujitsu_laptop         18504  0 
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                140131  0 

```


cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

```


ping -c 4 google.com

```
ping: unknown host google.com

```



Thanks a lot for your help!!!

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Networking & Wireless**.*

Welcome to the forum. Your post has been moved to its own thread. The title of the other matched your problem but that is it. Different computer, different config, different issues. Please refrain from hijacking existing posts. It is unfair to original OP, confusing and dilutes community effort. Post a new thread with a title that describes your problem exactly and include as much info as poss. It will increase your chances of help rather than being buried 56 posts deep on someone else's. 

Thanks and good luck.

---

### Post by Hadaka on 2013-05-23
Hi, it changed to..
```
[I]sudo modprobe -rfv iwlwifi
sudo modprobe -v [/I]*iwlwifi 11n_disable=1*
```

---

### Post by Bucky Ball on 2013-05-23
> **Hadaka said:**
> Hi, it changed to..
```
[I]sudo modprobe -rfv iwlwifi
sudo modprobe -v [/I]*iwlwifi 11n_disable=1*
```

And did it work?

---

### Post by stellar ashes on 2013-05-24
Hi, 
that works perfectly. 
Thanks a lot for the fast and accurate help!
Have a wonderful day.

P.S. Sorry for my ignorance and hijacking the other thread originally. I thought it would fit there...

---

### Post by Bucky Ball on 2013-05-24
No probs. Just a heads up to a new forum user. ;)

To help others please mark thread as solved by following the link in my thread and enjoy the Linux learning curve.

---

