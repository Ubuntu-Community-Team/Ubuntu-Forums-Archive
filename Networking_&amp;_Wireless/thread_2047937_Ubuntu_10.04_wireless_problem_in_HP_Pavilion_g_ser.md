---
title: "Ubuntu 10.04 wireless problem in HP Pavilion g series laptop"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by killarneya on 2012-08-25
I'm a brand-new user to ubuntu; I'm taking an introductory programming course and we've only had one lesson so far. My university teacher gave us usb drives with ubuntu 10.04 pre-loaded on them; this is what I'm using. I have a HP Pavilion g series laptop. 

When I boot into ubuntu's system, my laptop will not register wireless connections even though the wifi works perfectly in windows. I can only access the internet when I plug in a cable. I've browsed the forums enough to know that it sounds like a common problem, but I haven't seen a thread that matches my laptop/ubuntu specifications. 

Here are my commands as recommended in the HOWTO thread. ([http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681))

Code **$ lspci**

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9649
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
00:11.0 SATA controller: Advanced Micro Devices [AMD] Device 7804
00:12.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Device 780b (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Device 780d (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Device 780e (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Device 780f (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:15.2 PCI bridge: Advanced Micro Devices [AMD] Device 43a2
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: RaLink Device 5390
08:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

**$ ifconfig**

eth2      Link encap:Ethernet  HWaddr 78:e3:b5:76:f9:24  
          inet addr:130.160.138.107  Bcast:130.160.139.255  Mask:255.255.254.0
          inet6 addr: fe80::7ae3:b5ff:fe76:f924/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13070441 (13.0 MB)  TX bytes:1174230 (1.1 MB)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

**$ lsmod**
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_idt      52074  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
uvcvideo               57438  0 
videodev               34457  1 uvcvideo
softcursor              1189  1 bitblit
v4l1_compat            13251  2 uvcvideo,videodev
rt5390sta            1450360  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
i2c_piix4               8335  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            40033  1 
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32680  0 

**$ sudo lshw -C network**
[sudo] password for ubuntu: 

**$ iwlist scan**
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

ra0       Interface doesn't support scanning.

**$ lsb_release -d**
Description:    Ubuntu 10.04.4 LTS

**$ uname -mr**
2.6.32-42-generic i686

Any and all help would be appreciated.

---

### Post by mörgæs on 2012-08-26
Hi, welcome to the fora.

If you are new to Ubuntu I would recommend that you begin with a fresh install of 12.04.

---

