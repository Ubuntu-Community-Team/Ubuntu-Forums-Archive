---
title: "Just got 12.04, have Penguin Wireless N USB Adapter, worked before, now issues"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by TMundo on 2012-07-30
Started with 10.04.  Had a Linksys E1000 wireless router.  was told I needed to buy a **Penguin Wireless N USB Adapter**   off of the ThinkPenguin website.  I did, but I couldn't get things   working until 11.04 came out.  After that all issues were solved and   things worked great.  When 12.04 came out, I thought about upgrading   and the problems it could create, but finally figured it wouldn't be the   Ubuntu Team's plan to move backward, so I upgraded.  Things worked fine   for a little while and then web pages stopped loading.

If I reset my internet connection in the Ubuntu menu in the upper right   hand corner (I log off, then log back on)  things work fine again for a   good 10-15 minutes.

It would seem that this problem occurs faster on sites that are   trafficing more info, for example, it takes a youtube video about 5   minutes to stop loading, or I simply open another youtube video at the   same time and the browser cannot connect to it until I reset the   connection.  A regular site containing only reading information with   limited animation doesn't give me trouble as fast.  As I am typing this I   have 2 other sites open containing only readable info, and yet I am   having no issues navigating the forum, but eventually I will have to   reset the internet connection.

the people at ThinkPenguin seem to think the wireless card is   malfunctioning, and that it isn't a result of the new upgrade to 12.04.    They also said that the card I bought from them gets more complaints   with my modem than its cheaper sister version, the **Penguin Wireless G USB Adapter.**   I bought the Wireless N Adapter because they initially told me it was   faster than the Wireless G Adapter and was only $10.00 more.  Now I'm   being told to buy the cheaper one too.  That's a bit annoying, so I   figured I'd check the forum before shelling out more cash.  It isn't a   lot of money, but I'd still like to know a little more before I buy   another Wireless card.

please explain how to fix this if you can...

---

### Post by Kirk Schnable on 2012-07-30
It would be helpful to have some specific information about your card.  Can you give us the output of:

```
lsusb
```

```
lshw -C network
```

Kirk

---

### Post by TMundo on 2012-07-30
After lsusb I get:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 003 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 005: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 802.11n [Atheros AR9170]


after  lshw -C network I get:


lshw -C network
 	Code:
 	WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:31:e2:ef
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5754-v3.13 latency=0 multicast=yes port=twisted pair
       resources: irq:46 memory:ecef0000-ecefffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:8
       logical name: wlan0
       serial: 00:22:2d:bf:f2:bb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=carl9170 driverversion=3.2.0-24-generic firmware=1.9.4 ip=192.168.1.142 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


-any help you could give me would be great

---

### Post by Kirk Schnable on 2012-07-30
The truth comes out.  Your "Penguin Wireless" card is an Atheros card.

Can you now get me:
```
modinfo carl9170
```

```
uname -r
```

Should help us find out if there's a later driver available for you.

Kirk

---

### Post by TMundo on 2012-07-30
"modinfo carl9170" gives me:

filename:       /lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
alias:          arusb_lnx
alias:          ar9170usb
firmware:       carl9170-1.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
author:         Christian Lamparter <chunkeey@googlemail.com>
author:         Johannes Berg <johannes@sipsolutions.net>
version:        1:1.9.4
srcversion:     D2411637BD7256187C65770
alias:          usb:v1B75p9170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8402d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8401d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0409p02B4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0409p0249d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp093Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0026d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3417d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1435p0326d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1435p0804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0ACEp1221d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:vCACEp0300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9170d*dc*dsc*dp*ic*isc*ip*
depends:        mac80211,ath,cfg80211
intree:         Y
vermagic:       3.2.0-24-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware crypto offload. (bool)
parm:           noht:Disable MPDU aggregation. (int)

"uname -r" gives:

3.2.0-24-generic

-it would be better than reinstalling 11.04 if there is another driver available.

-thanx

---

### Post by Kirk Schnable on 2012-07-30
Can you give me the output of:
```
lsmod
```

I saw this thread, about someone in a similar situation: [http://ubuntuforums.org/showthread.php?t=1640053&page=2](http://ubuntuforums.org/showthread.php?t=1640053&page=2)

I want to see, among other things, if the ar9170usb module happens to be loaded.

Kirk

---

### Post by chili555 on 2012-07-30
> I want to see, among other things, if the ar9170usb module happens to be loaded.There is no ar9170usb natively in 12.04.

---

### Post by Kirk Schnable on 2012-07-30
> **chili555 said:**
> There is no ar9170usb natively in 12.04.

Ah, alright, wasn't aware of that.  Thanks Chili555.

---

### Post by TMundo on 2012-07-31
And I get back to you in 24 hrs (sorry, life is tiring sometimes)

lsmod:

Module                  Size  Used by
arc4                   12473  2 
carl9170               77667  0 
mac80211              436455  1 carl9170
ath                    19387  1 carl9170
cfg80211              178679  3 carl9170,mac80211,ath
snd_usb_audio         101566  1 
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
rfcomm                 38139  4 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_pcm                80845  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
dcdbas                 14098  0 
snd_seq_midi           13132  0 
psmouse                87213  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
binfmt_misc            17292  1 
gspca_zc3xx            51066  0 
serio_raw              13027  0 
gspca_main             27654  1 gspca_zc3xx
videodev               86588  1 gspca_main
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
usbhid                 41906  0 
hid                    77367  1 usbhid
nouveau               708198  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  19 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65344  1 nouveau
mac_hid                13077  0 
drm_kms_helper         45466  1 nouveau
drm                   197692  4 nouveau,ttm,drm_kms_helper
i82975x_edac           12911  0 
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
edac_core              46858  1 i82975x_edac
video                  19068  1 nouveau
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
sata_via               13495  0 
tg3                   137273  0

---

### Post by TMundo on 2012-07-31
I read the forum post and the link within the forum post.  Although I am working in 12.04 and that guy's issue was with Natty, I think it is safe to say that with every new upgrade there seems to be new issues, depending on what type of hardware you are dealing with.

I started out with an earlier version of Ubuntu that did not work, with this Atheros card.  I ended up having it sit around the house installed alongside windowsXP.  When the next release of Ubuntu came out the problem was resolved.  Now I jumpped the gun and upgraded to 12.04 and although it still works, it works intermittantly.

Its funny, when I leave the wireless card plugged in for a few hours, I get strange variations of my own network name listed under my network.  For example, if my network name was JMANSAY, after a few hours of being connected. without using the connection, I would se multipule variations of other supposed networks in the area, such as JWANSAY, J#WANSAY, JH8NSAY, etc.  I assumed it was the likes of a hacker in the area trying to get me to click on the wrong network name by accident.  

Asside from that, (that may be a separate issue) something has been changed with the new release, it would seem as so.

---

