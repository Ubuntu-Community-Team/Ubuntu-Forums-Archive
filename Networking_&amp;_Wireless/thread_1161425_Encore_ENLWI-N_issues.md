---
title: "Encore ENLWI-N issues"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by dbloom on 2009-05-16
Hi,

Just go this card recently and set it up this morning.  It was recognized right away (as ra0) and I could see networks, but I couldn't connect to mine.  I made the network completely unprotected and still couldn't connect.  

I tried grabbing the windows driver, but ndiswrapper wouldn't recognize it as a valid driver.  I tried the rt2860 driver on launchpad (deb file), but that didn't work either.  In trying all these things, I lost the interface -- ra0 no longer exists and the network is now UNCLAIMED.  

Below is my info.  I'm hoping someone much smarter than I am can help.  My brain is beginning to hurt.  Thanks all!

```
1 ) Machine Brand and Model (PC/Laptop):

ABIT NF7Sv2 (athlon xp 2500+)

2 ) Wireless Brand, Model and Wireless Chipset:

Encore 
ENWLI-N
rt2860



$ lspci

01:09.0 Network controller: RaLink RT2800 802.11n PCI

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

3 ) check interface:
Code:

$ ifconfig
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:50:8d:e3:e9:61  
          inet addr:192.168.10.198  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fee3:e961/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3531897 (3.5 MB)  TX bytes:502152 (502.1 KB)
          Interrupt:22 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:540 (540.0 B)  TX bytes:540 (540.0 B)
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

4 ) Check for modules:

$ lsmod
$ lsmod | grep "wlan_module_name"

(sorry for the full listing)
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
w83627hf               31632  0 
hwmon_vid              11264  1 w83627hf
lm83                   16276  0 
sbp2                   30476  0 
lp                     17156  0 
iptable_nat            13700  0 
nf_nat                 25876  1 iptable_nat
nf_conntrack_ipv4      21388  3 iptable_nat,nf_nat
nf_conntrack           72008  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
iptable_mangle         10880  0 
iptable_filter         10752  0 
ip_tables              19472  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               23044  2 iptable_nat,ip_tables
snd_intel8x0           37532  3 
ppdev                  15620  0 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
pcspkr                 10496  0 
serio_raw              13316  0 
nvidia               7233756  36 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           193436  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
shpchp                 40212  0 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
joydev                 18368  0 
i2c_nforce2            14980  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
nvidia_agp             14492  1 
agpgart                42696  2 nvidia,nvidia_agp
hid_logitech           16256  0 
ff_memless             13320  1 hid_logitech
usbhid                 42336  1 hid_logitech
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
forcedeth              61712  0 
floppy                 64324  0 
vesafb                 13828  1 
fbcon                  46112  72 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

5 ) Kernel boot messages

$ dmesg

dmesg | grep pan0
[  537.916017] pan0: no IPv6 routers present

6 ) Network configuration
Code:

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:50:8d:e3:e9:61
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.10.198 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:9e:a8:60:bc:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

7 ) Scan for networks:

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

8 ) Ubuntu Version:
Code:

$ lsb_release -d
Description:	Ubuntu 9.04

9 ) Kernel/architecture (including 32 vs. 64 bit):

$ uname -mr
2.6.28-11-generic i686

10 ) Restarting the network:
Code:

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

```

---

### Post by dbloom on 2009-05-16
Ok, i just read through the "comprehensive ndiswrapper troubleshooting guide" and figured out how to install the windows driver.  unfortunately, now that it installs, it says it can't see if the hardware is present, which i assume is related to the network being unclaimed.  i guess a driver isn't claiming the network card (is that it?).  

thanks.

---

### Post by dbloom on 2009-05-16
Now, I reinstalled that deb file (from [https://launchpad.net/~stgraber/+archive/ppa]("https://launchpad.net/~stgraber/+archive/ppa")) And I actually connected to my network. using wpa encryption too. 

unfortunately, i'm connected as as 802.11g, not 802.11n.  

i guess this could be related to the driver, but i'm not sure.  any ideas on how to get the n network running?

thanks!

---

