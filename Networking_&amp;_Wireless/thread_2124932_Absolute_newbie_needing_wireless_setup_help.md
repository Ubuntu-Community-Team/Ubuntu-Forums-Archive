---
title: "Absolute newbie needing wireless setup help"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by panchogw on 2013-03-12
Hi forum people!

I'm an absolute newb to Ubuntu and Linux in general and need a hand to set up my wireless internet access. I spent the best part of yesterday going through the forums and trying various things but not really getting anywhere so any help would be much appreciated. So...

I'm on an old Dell Lattitude D810 and I dual boot alongside windows xp. From reading other posts the a starting point seems to be the command: sudo lshw -c network, which gives the following output. Thanks in advance.

*-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:d6:13:d4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=5751-v3.29a ip=192.168.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=wl latency=64
       resources: irq:17 memory:dfbfe000-dfbfffff
  *-network
       description: Ethernet interface
       physical id: 2
       bus info: usb@1:5
       logical name: eth1
       serial: d2:23:db:45:d6:30
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth link=no multicast=yes

---

### Post by Hadaka on 2013-03-12
Hi, lets first see what you may have possibly tried.
please post..

```
lsmod
```
thanks.

---

### Post by panchogw on 2013-03-12
> **Hadaka said:**
> Hi, lets first see what you may have possibly tried.
please post..

```
lsmod
```
thanks.

Thanks for the quick reply. That command gives me this:

cfg80211              181041  1 wl
ttm                    76326  1 radeon
video                  19117  0 
irda                  185617  0 
lib80211               14041  1 wl
yenta_socket           27465  0 
drm_kms_helper         47459  1 radeon
pcmcia_rsrc            18368  1 yenta_socket
snd                    62675  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   240232  5 radeon,ttm,drm_kms_helper
pcmcia_core            21512  3 pcmcia,yenta_socket,pcmcia_rsrc
crc_ccitt              12628  1 irda
mac_hid                13078  0 
soundcore              14636  1 snd
lpc_ich                16993  0 
snd_page_alloc         14109  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13317  1 radeon
parport_pc             32115  0 
ppdev                  12850  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
tg3                   141717  0

---

### Post by Hadaka on 2013-03-12
Hi, please do.

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```

please post back the results.
*If the wireless activates, please use thread tools and mark solved
thanks.

---

### Post by panchogw on 2013-03-12
Works like a dream! You're awsome thanks! =D>

---

### Post by Hadaka on 2013-03-12
Hi, glad that workd for you. please do.

```
echo "b43" | sudo tee -a /etc/modules
```

this will make sure the driver is loaded on boot.
also..please use thread tools to mark this SOLVED
and....
Welcome to the forums.
have fun !

---

