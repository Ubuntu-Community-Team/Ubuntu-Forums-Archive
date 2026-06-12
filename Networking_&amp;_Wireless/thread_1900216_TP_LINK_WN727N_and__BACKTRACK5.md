---
title: "TP LINK WN727N and  BACKTRACK5"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by humamiaz on 2011-12-25
is it compatible and how i install im not sure help me pls 

ps: im new to ubuntu :s

---

### Post by wildmanne39 on 2011-12-25
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
lsusb
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by humamiaz on 2012-01-04
hi there im the real ubuntu noob but googlling im trying to set up this wifi usb
god know how many hours i spent just to install it, but now i cant set a channel in mon0

Interface    Chipset        Driver

wlan0        Unknown     rt2800usb - [phy1

i think the problem is something about this 

pls help :s

---

### Post by coffeecat on 2012-01-05
@humamiaz, I've merged your two threads which you made a week apart and which appear to be about the same issue. If you post the output wildmanne39 suggested, then someone may be able to help you.

Are you using Ubuntu or Backtrack, which is mentioned in your original thread title?

---

### Post by humamiaz on 2012-01-05
im using ubuntu 10.11

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
hugo@ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:0ded]
    Kernel driver in use: r8169
hugo@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

hugo@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. 
Bus 002 Device 002: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
hugo@ubuntu:~$ rfkill list all
hugo@ubuntu:~$ lsmod
Module                  Size  Used by
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
isofs                  40253  1 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
lp                     17799  0 
binfmt_misc            17540  1 
adt7475                31231  0 
hwmon_vid              12746  1 adt7475
snd_hda_codec_realtek   330769  1 
nouveau               728662  3 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
snd_hwdep              13668  1 snd_hda_codec
drm                   236330  5 nouveau,ttm,drm_kms_helper
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i2c_algo_bit           13423  1 nouveau
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
mxm_wmi                12979  1 nouveau
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
option                 25477  2 
wmi                    19256  1 mxm_wmi
usb_wwan               20491  1 option
usbhid                 47198  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbserial              47107  7 option,usb_wwan
ppdev                  17113  0 
soundcore              12680  1 snd
video                  19412  1 nouveau
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
hid                    95463  1 usbhid
parport_pc             36962  1 
parport                46562  3 lp,ppdev,parport_pc
usb_storage            57901  1 
uas                    18027  0 
floppy                 70365  0 
r8169                  52788  0 
hugo@ubuntu:~$

---

### Post by humamiaz on 2012-01-05
mon0 is on channel -1, but the AP uses channel 6

Interface    Chipset        Driver

wlan0        Unknown     rt2800usb - [phy0]
mon0        Unknown     rt2800usb - [phy0]

i guess the problems is arround this

somebody help me pls...

---

### Post by Basher101 on 2012-01-05
you need to set the mon0 manually on the channel.
do this by typing these commands```
sudo ifconfig mon0 down
sudo iwconfig mon0 mode managed
sudo ifconfig mon0 up
sudo iwconfig mon0 channel 6
sudo ifconfig mon0 down
sudo iwconfig mon0 mode monitor
sudo ifconfig mon0 up
```

and you are done setting the channel.

to undo this type ```
sudo ifconfig mon0 down
sudo iwconfig mon0 mode managed
sudo ifconfig mon0 up
```

regards


p.s. are you using the right driver? it should be the rtl8169 driver

---

### Post by humamiaz on 2012-01-05
root@ubuntu:/home/hugo# ifconfig mon0 down
root@ubuntu:/home/hugo# iwconfig mon0 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; Device or resource busy.

---

