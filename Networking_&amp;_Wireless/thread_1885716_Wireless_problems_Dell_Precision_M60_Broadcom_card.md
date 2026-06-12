---
title: "Wireless problems Dell Precision M60 Broadcom card"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by lsward on 2011-11-23
I'm having wireless problems with my Dell Precision M60 when I upgraded to 11.10.  I looked through a number for threads and some of the documentation.  I still can't get this thing to work.  I ran a couple of terminal commands and here is the output.

cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux feather-Precision-M60 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux
```

sudo lshw -C network
```
*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1a:77:00
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=5705-v3.11 ip=192.168.1.101 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafec000-fafedfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:b3:da:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
feather@feather-Precision-M60:~$ lspci -nn | grep -e 0280 -e 0200
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

```

rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

lsmod
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  2 
joydev                 17393  0 
b43                   318816  0 
ppdev                  12849  0 
snd_intel8x0           33318  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nouveau               663211  2 
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              393459  1 b43
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
psmouse                73673  0 
cfg80211              172392  2 b43,mac80211
snd                    55902  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
serio_raw              12990  0 
drm                   192226  4 nouveau,ttm,drm_kms_helper
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
parport_pc             32114  1 
wmi                    18744  1 mxm_wmi
video                  18908  1 nouveau
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
tg3                   132972  0 
ssb                    50682  1 b43
crc_itu_t              12627  1 firewire_core

```

sudo iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

Any suggestions.  Thanks.

---

### Post by fdrake on 2011-11-23
can you post the result for
```

sudo ifconfig -v wlan0 up

```

also if you don't get any results post
```

less /etc/NetworkManager/nm-system-settings.conf

```

---

### Post by lsward on 2011-11-23
This is what I got.

sudo ifconfig -v wlan0 up
```
SIOCSIFFLAGS: No such file or directory
WARNING: at least one error occured. (-1)

```


less /etc/NetworkManager/nm-system-settings.conf
```
/etc/NetworkManager/nm-system-settings.conf: No such file or directory

```

Doesn't look to good.

---

### Post by fdrake on 2011-11-23
what is more interesting is that lshw is showing 3 network controllers.... hmm. can you try at boot-time to login in an older kernel and see if the wifi works with any of them . if so we can install the backports and update/upgrade the system from that working kernel.

in the meantime can you also check that you don't have a switcher (or a Bios-option)that is locking the wifi. wlan0 shows up as "DISABLED" for some reason.

---

### Post by lsward on 2011-11-23
The funny thing is that when I was running Xubuntu before I upgraded to 11.10 the wireless worked fine.  I'll try booting into a older kernel first though.

---

### Post by lsward on 2011-11-23
I just booted into an older kernel version and wireless is still down.

---

### Post by fdrake on 2011-11-23
i do believe the problem is in the firmware: try this
```

sudo apt-get install b43-fwcutter firmware-b43-installer
sudo reboot now

```
if still not luck post again your
```

lsmod
sudo lshw -C network

```

---

### Post by lsward on 2011-11-23
Still no luck.

lsmod
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  2 
b43                   318816  0 
mac80211              393459  1 b43
joydev                 17393  0 
ppdev                  12849  0 
snd_intel8x0           33318  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dcdbas                 14098  0 
nouveau               663211  2 
pcmcia                 39822  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              172392  2 b43,mac80211
psmouse                73673  0 
drm                   192226  4 nouveau,ttm,drm_kms_helper
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              12990  0 
snd                    55902  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
parport_pc             32114  1 
video                  18908  1 nouveau
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          35854  0 
tg3                   132972  0 
ssb                    50682  1 b43
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

```

 sudo lshw -C network
```
 *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:1a:77:00
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 duplex=full firmware=5705-v3.11 ip=192.168.1.101 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:fafec000-fafedfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:b3:da:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by lsward on 2011-11-23
I'm going to try ndiswrapper.

---

### Post by lsward on 2011-12-04
I'm not having any luck with this thing.  Anyone else what to take a crack at making this laptop submit to my demands for wireless?

---

