---
title: "Wireless won't work in Ubuntu 10.4 NBE with 802.11n Lan Card"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by Anacreon on 2010-07-17
I recently installed Ubuntu 10.4 Netbook Edition on my Sony Vaio alongside Win7 Starter with the intention of eventually losing the latter altogether. I'm being stopped by an inability to connect to my home wireless network.
  I have a Sony Vaio VPCM11M1E with an 802.11n Wireless Lan Card and a home network provided by Sky via a Netgear router with WAP-Personal security and TKIP encryption (all according to Windows). It connects fine in Windows (7, XP and VISTA on various computers) but in Ubuntu I put in the network name & key and get a small window in the top right-hand corner saying: ***"Wireless Network disconnected – you are now offline” ***and it won't do anything else. Wireless is enabled and the connection is set to connect automatically. That said, the menu in the top right corner doesn't identify the sky network at all even after I’ve entered connection settings manually.
  I found this guide**
***[http://ubuntuforums.org/showthread.php?t=1476007&nojs=1#helpmenu](http://ubuntuforums.org/showthread.php?t=1476007&nojs=1#helpmenu)*

and thought it might help, but I've spent two days trying to get past step 5 and can't get to grips with it. But I’m not at all sure that that's not running ahead of myself. Shouldn't Ubuntu at least see the network as Windows does, and then prompt me for the network key?
  I’ve never used Ubuntu or anything other than Windows before, so please patronise if you think I’m missing something obvious.

---

### Post by xivaj on 2011-09-21
Hi,

yes, it works. You have to follow the tutorial but replacing the wifi card model he uses (rt2860) with the one you may have. In my case it is rt3090. I have a vaio VPCM11M1E with ubuntu netbookedition 10.04 and it works perfectly. 

If you want to know which is your car execute on a terminal
```

lshw -c network
```


Cheers

---

### Post by wildmanne39 on 2011-09-21
Hi, we need to find out a few things please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by jas1291 on 2011-09-24
first i am using a pc
second i am using edimax usb router
i am experiencing same problem. it shows i am connected to wireless network. i can ping my dns but i cant connect to any other site....pls help i have even tried to manuall enter all ip info
pls see this
```
jasleen@jasleen-desktop:~$ uname -a
Linux jasleen-desktop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
jasleen@jasleen-desktop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Atheros Communications L2 100 Mbit Ethernet Adapter [1969:2048] (rev a0)
	Kernel driver in use: atl2
	Kernel modules: atl2
jasleen@jasleen-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 7392:7811  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jasleen@jasleen-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203376  1 
ndiswrapper           184677  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
8192cu                247698  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
i915                  288611  3 
drm_kms_helper         29329  1 i915
parport_pc             25962  1 
asus_atk0110            9017  0 
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
atl2                   22383  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
output                  1871  1 video
parport                32635  3 ppdev,parport_pc,lp
floppy                 53016  0 
jasleen@jasleen-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UTStarcom"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F7:2E:4D   
          Bit Rate:48 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-45 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jasleen@jasleen-desktop:~$ rfkill list
jasleen@jasleen-desktop:~$ sudo iwlist scan
[sudo] password for jasleen: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:57:F7:2E:4D
                    ESSID:"UTStarcom"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=100/100 
```

---

### Post by wildmanne39 on 2011-09-24
Hi, welcome to the forum! let's start by removing ndiswrapper,please do this.
```
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
then unplug your wired connection and do this please:
```
sudo modprobe 8192cu
```
Does that make it turn on?
Thank you

---

