---
title: "Please Help Atheros Problem"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by weman101 on 2010-08-24
I have a toshiba satelitte A135-S4656 and i cannot connect to my wireless internet i have tried madwifi but idk how to do it so if i messed something up and i need to reinstall ubuntu plz tell me, i am running ubuntu 10.04
lspci retutns - Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
ifconfig returns- eth0      Link encap:Ethernet  HWaddr 00:1b:38:41:47:9f  
          inet addr:192.168.1.92  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe41:479f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8286280 (8.2 MB)  TX bytes:1270220 (1.2 MB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

iw config returns - weman101@weman101-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

lsmod returns-

weman101@weman101-laptop:~$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   203168  1 
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
arc4                    1153  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
joydev                  8708  0 
pcmcia                 33024  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
drm_kms_helper         29297  1 i915
yenta_socket           20408  1 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               3690  0 
sdhci_pci               5470  0 
rsrc_nonstatic         10015  1 yenta_socket
drm                   162471  4 i915,drm_kms_helper
sdhci                  15462  1 sdhci_pci
intel_agp              24177  2 i915
tifm_core               6045  1 tifm_7xx1
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class               2864  1 sdhci
psmouse                63245  0 
serio_raw               3978  0 
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
r8169                  33884  0 
mii                     4381  1 r8169

---

