---
title: "edimax usb router connected but no internet connection"
date: 2011-09-24
forum: Networking &amp; Wireless
---

### Post by jas1291 on 2011-09-24
hi i am using ubuntu 10.04. i am very new to ubuntu.
i bought a edimax usb router. after quite searching i installed its driver. now it works well. but the problem is although it shows that it is connected to the network i cant access network. my ip, subnet, dns settings are all fine i checked. wired connection is working pretty well........pls help

---

### Post by praseodym on 2011-09-24
Hi,

please show the terminal outputs of

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by jas1291 on 2011-09-24
```
jasleen@jasleen-desktop:~$ lspci -nnk | grep - iA2 net
grep: iA2: No such file or directory
grep: net: No such file or directory
jasleen@jasleen-desktop:~$ sudo su
[sudo] password for jasleen: 
root@jasleen-desktop:/home/jasleen# lspci -nnk | grep - iA2 net
grep: iA2: No such file or directory
grep: net: No such file or directory
root@jasleen-desktop:/home/jasleen# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 7392:7811  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@jasleen-desktop:/home/jasleen# lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
8192cu                247698  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   5259  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288611  3 
drm_kms_helper         29329  1 i915
ndiswrapper           184677  0 
parport_pc             25962  1 
asus_atk0110            9017  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7028  0 
drm                   162377  4 i915,drm_kms_helper
psmouse                63677  0 
serio_raw               3978  0 
atl2                   22383  0 
intel_agp              24375  2 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  3 ppdev,parport_pc,lp
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
floppy                 53016  0 
root@jasleen-desktop:/home/jasleen# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UTStarcom"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F7:2E:4D   
          Bit Rate:48 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=-46 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@jasleen-desktop:/home/jasleen# rfkill list
root@jasleen-desktop:/home/jasleen# cat rfkill list
cat: rfkill: No such file or directory
cat: list: No such file or directory
root@jasleen-desktop:/home/jasleen# sudo iwlist scan
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
          Cell 02 - Address: 00:25:5E:17:43:08
                    ESSID:"Airtel"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=43/100  Signal level=43/100  

root@jasleen-desktop:/home/jasleen# 

```

---

### Post by praseodym on 2011-09-24
Uninstall ndiswrapper:


```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```
and reboot. Try WPA2-AES (CCMP) encryption instead of "none".

---

### Post by jas1291 on 2011-09-27
nothing happened..........i am really pissed..........it works sometimes i dont know how........but i need all time access.........pls somebody help..........ready to give any info u need...........

---

### Post by praseodym on 2011-09-27
Ok,

check:

```
iwconfig
rfkill list
lsmod
dmesg | grep 81
sudo iwlist scan
route -n
```

---

