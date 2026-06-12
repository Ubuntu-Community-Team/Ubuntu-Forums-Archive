---
title: "Ubuntu 10.04 Wireless Help"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by jjmono987 on 2011-07-24
I have installed ubuntu 10.04 and i am wondering how to get my wireless to work. I am running a Dell Inspiron 9100 with a broadcom wireless card. and i see that it recognizes the wireless i just cant seem to get connected tot he internet with it. So please help me out thanks.

---

### Post by wildmanne39 on 2011-07-24
Hi, run these commands in a terminal please
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list All
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by moonsal on 2011-07-24
Here ya go..... Make sure you copy your wireless '"driver".inf' file to a usb,etc. and have it handy.... Worked wonders on this end...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jjmono987 on 2011-07-24
> ~$ lspci -nn | grep 0280
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

> ~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.


> [QUOTE]:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no[/QUOTE]


> ~$ lsmod
Module                  Size  Used by
ndiswrapper           184677  0 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
usb_storage            39841  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
rfcomm                 33421  4 
sco                     7917  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_oss            26722  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
radeon                678735  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43legacy             115152  0 
ttm                    50103  1 radeon
snd_timer              19098  2 snd_pcm,snd_seq
pcmcia                 30784  0 
drm_kms_helper         29329  1 radeon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           20408  1 
mac80211              205402  1 b43legacy
rsrc_nonstatic         10015  1 yenta_socket
drm                   162377  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
joydev                  8740  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
cfg80211              126144  2 b43legacy,mac80211
led_class               2864  1 b43legacy
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 28835  0 
intel_agp              24375  1 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
btusb                  11053  2 
video                  17375  0 
output                  1871  1 video
psmouse                63677  0 
dell_wmi                1793  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dcdbas                  5422  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
b44                    25574  0 
ieee1394               81181  1 ohci1394
ssb                    38934  2 b43legacy,b44
mii                     4381  1 b44



Okay here it is

---

### Post by wildmanne39 on 2011-07-24
Hi, run this in a terminal please
```
sudo apt-get autoremove ndiswrapper
```
Restart your computer after running this command.
Thank you

---

