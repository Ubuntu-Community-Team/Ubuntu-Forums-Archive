---
title: "No wired connection"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by ferruccio.sarra on 2011-09-10
Hi all,
I haven't been using Ubuntu and Linux distro in general for a long time so I will cenrtanly submit a trivial issue. Already installed 10.04 on my new ThinkPad T420. After system updating everything but the wired connection seems going right. I report here the "lshw" and the content of "/etc/network/interfaces". Some  suggestion on how to install eth card driver? 
Thank you.

CCC@ttt-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f3900000-f391ffff memory:f392b000-f392bfff ioport:6080(size=32)
  *-network
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:ae:9b:aa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.2 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:30 memory:f3800000-f3801fff
ferruccio@ferruccio-laptop:~$

---

### Post by ferruccio.sarra on 2011-09-10
...forgot the interfaces file content:

auto lo
iface lo inet loopback

---

### Post by praseodym on 2011-09-10
Hi,

üplease show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
```

---

### Post by ferruccio.sarra on 2011-09-10
Thank you for replying praseodym! Here I am:

ccc@ttt-laptop:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
	Kernel driver in use: ehci_hcd
--
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 1000 Series [8086:0084]
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn


###############################################################

ccc@ttt-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
arc4                    1153  2 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                106911  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               106149  1 iwlagn
mac80211              205402  2 iwlagn,iwlcore
nouveau               467048  0 
snd                    54244  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    50103  1 nouveau
led_class               2864  1 iwlcore
drm_kms_helper         29329  1 nouveau
cdc_wdm                 8218  0 
cdc_acm                14754  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
tpm_tis                 7488  0 
tpm                    13936  1 tpm_tis
tpm_bios                5266  1 tpm
video                  17375  0 
fbcon                  35102  71 
output                  1871  1 video
tileblit                1999  1 fbcon
psmouse                63677  0 
font                    7557  1 fbcon
serio_raw               3978  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
cfg80211              126144  3 iwlagn,iwlcore,mac80211
drm                   162377  3 nouveau,ttm,drm_kms_helper
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
vga16fb                11385  1 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32360  3 

###############################################################

ccc@ttt-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1408 (1.4 KB)  TX bytes:1408 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:ae:9b:aa  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8ea9:82ff:feae:9baa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:463520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:669137122 (669.1 MB)  TX bytes:29760711 (29.7 MB)

---

### Post by praseodym on 2011-09-10
In 10.04 your device ID is not part of the module e1000e (checked it here). You may want to install the driver by hand:

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

Please use the long "sudo rm"-commands **without** "-rf" at the end. Copy/paste also works in the terminal.

Needed for installation:

```
sudo apt-get install linux-headers-generic build-essential dkms
```

Use the newest driver available from that link and adjust the folder names.

---

