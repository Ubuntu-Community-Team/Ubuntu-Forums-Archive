---
title: "Wireless went down."
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by LostMagix on 2008-12-11
I'm not going to lie, the wireless on this laptop ([Compaq Presario F700]("http://h10025.www1.hp.com/ewfrf/wc/product?product=3629568&lc=en&cc=us&dlc=en&lang=en&cc=us")) has given me nothing but problems. The wireless card is seen as an "Atheros ar242x 802.11abg" but after some searching I found that there were no windows drivers for that card so I tried to take I another path and I found out that the "Atheros ar5007" wireless card will show up as an "Atheros ar242x". 
 
    I found the windows driver for the ar5007 and use the net5211.inf in "windows wireless drivers" Immediately after I did this the wireless network did not connect but later that day it just started to work.

   Last night it stoped work and i have no idea why, I redid everything I did before but I cant seem to get the wireless to work

---

### Post by LostMagix on 2008-12-12
*bump*


PS:This is a friends laptop so i only have access to it when im around him. It may take a while to get back to you.

---

### Post by LostMagix on 2008-12-14
*bump

---

### Post by theytookpenny on 2008-12-14
I had a similar problem and fixed it. if you're using the Network Manager that came installed on the original cd, [this thread]("http://ubuntuforums.org/showthread.php?t=1010510") might be able to help you. Go to the 6th post.

---

### Post by LostMagix on 2008-12-14
Didnt do a whole lot, now I cant see the wireless network at all. I have tried madwifi, ndiswrapper and a few other programs.

A few outputs:

```
$ lsmod
Module                  Size  Used by
isofs                  44072  1 
udf                    93480  0 
crc_itu_t              10496  1 udf
af_packet              29568  2 
binfmt_misc            18700  1 
sco                    20612  2 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 sco,rfcomm,bnep,l2cap
ipv6                  314312  14 
ppdev                  16904  0 
powernow_k8            23684  1 
cpufreq_ondemand       16400  1 
cpufreq_powersave      10368  0 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
freq_table             13568  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    16392  0 
container              12288  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
psmouse                51612  0 
pcspkr                 11136  0 
snd_hda_intel         489264  2 
ndiswrapper           253696  0 
serio_raw              14596  0 
evdev                  20512  11 
nvidia               7804864  38 
k8temp                 13568  0 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
i2c_core               36128  1 nvidia
video                  28948  5 
output                 11776  1 video
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
shpchp                 42140  0 
snd_seq_midi           15872  0 
pci_hotplug            39472  1 shpchp
sdhci_pci              17024  0 
sdhci                  27396  1 sdhci_pci
wmi                    15808  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
ricoh_mmc              12672  0 
mmc_core               67168  1 sdhci
ac                     13448  0 
button                 15904  0 
battery                21128  0 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sd_mod                 45864  3 
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod
crc_t10dif             10240  1 sd_mod
usbhid                 39776  0 
hid                    59072  1 usbhid
sg                     45408  0 
pata_acpi              13568  0 
ata_generic            14212  0 
pata_amd               22020  1 
ahci                   43148  2 
libata                200160  4 pata_acpi,ata_generic,pata_amd,ahci
forcedeth              68112  0 
scsi_mod              183160  4 sd_mod,sr_mod,sg,libata
dock                   18464  1 libata
ehci_hcd               48908  0 
ohci_hcd               34972  0 
usbcore               175376  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
thermal                27424  0 
processor              47800  4 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 

```

```
$ lspci

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


```

```
$ lsmod | grep "ath"
:~$ 

```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

```
$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:f8:72:b3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:01:1f:a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:85:e1:5f:88:30
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
kc@kc-laptop:~$ 

```



As I look more and more into this, I'm thinking one of the updates may have done it. I found [this thread]("http://ubuntuforums.org/showthread.php?t=1003413&highlight=Atheros+AR242x+Wireless")


I have seen 3 other threads with people having the same problem.

---

