---
title: "Can't set up a wired/wireless internet connection on Ubuntu 10.04"
date: 2011-10-13
forum: Networking &amp; Wireless
---

### Post by Usagi_ on 2011-10-13
Hi, I have a Packard Bell OneTwo  L i7526 with ubuntu 10.04. I can't connect to the internet using a wireless connection because under network connection it says "device not ready". So i bought an ethernet cable but still there are no network connections displayed. 
I'll copy here all the info required for a wireless thread. 
Thanks a lot for your help 

```
§ lspci

00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c4a (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
02:00.0 Multimedia controller: Philips Semiconductors Device 7160 (rev 03)

$ lsusb
Bus 002 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0408:3003 Quanta Computer, Inc. 
Bus 001 Device 004: ID 04f2:b28b Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04ca:0058 Lite-On Technology Corp. 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:888 errors:0 dropped:0 overruns:0 frame:0
          TX packets:888 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69808 (69.8 KB)  TX bytes:69808 (69.8 KB)

$ iwconfig wlan0
wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod
Module                  Size  Used by
pppoe                   8368  0 
pppox                   2074  1 pppoe
r8192s_usb            346908  0 
usb_storage            39841  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio          75765  1 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_usb_lib            15801  1 snd_usb_audio
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
joydev                  8740  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd_hwdep               5412  2 snd_hda_codec,snd_usb_audio
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
psmouse                63677  0 
serio_raw               3978  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54244  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_rawmidi,snd_hwdep,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  2 

$ iwlist scan

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down
```

---

### Post by Usagi_ on 2011-10-15
Can  anyone please help me?

---

### Post by praseodym on 2011-10-15
Can you show:

```
lspci -nnk | grep -iA2 net
rfkill list
iwconfig
```
Normally you only need to copy the firmware for the stick to a new place:

```
sudo mkdir /lib/firmware/RTL8192SU
sudo cp /lib/firmware/RTL8192SE/rtl8192sfw.bin /lib/firmware/RTL8192SU/ 
```
and replug the stick

---

### Post by ajsoulmate on 2011-10-17
please post the output of:


```
sudo lshw -C network
```

---

