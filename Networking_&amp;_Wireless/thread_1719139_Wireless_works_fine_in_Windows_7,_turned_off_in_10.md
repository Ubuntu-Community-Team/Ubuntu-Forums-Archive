---
title: "Wireless works fine in Windows 7, turned off in 10.10"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by Replicounts on 2011-04-01
I've been happily using 10.10 Desktop Edition alone for months on an Asus Eee, but got a new Eee (1015PEM-PU17), and this time want to have dual boot with Windows 7. I used the Wubi downloader, and everything works in Windows 7, and almost everything in Ubuntu.

But the wireless in Ubuntu won't turn on. The wireless icon is in the taskbar, showing as disconnected, but it won't discover any of the many (password protected) wi-fi signals in my neighborhood. It never asked me for my wi-fi password. None of the options in either right-click or left-click on the wireless icon help (and oddly, I can't remove that icon from the taskbar, as usually possible with a right click). Of course I tried the Network settings under both Preferences and Administration, but couldn't find a way to turn on the wireless there.

One hint: in gconf-editor on the older Eee that does work, under "system" there are six folders, including "networking". In the new Eee, that "networking" folder is missing (only the other five folders are there).

All I want is dual boot on this popular Eee machine. It's not a hardware problem, since the same wireless works fine in Windows. Does anyone know how to fix this, and get the wireless turned on in Ubuntu?


Wireless Info:


$ lspci
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)



$ lsusb
Bus 005 Device 002: ID 13d3:3315 IMC Networks 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5702 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



$ ifconfig
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:d0:80:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)



$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



$ lsmod
Module                  Size  Used by
rfcomm                 40755  0 
binfmt_misc             7984  1 
sco                     9954  0 
bnep                   11985  0 
l2cap                  42304  4 rfcomm,bnep
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11363  0 
snd_hda_codec_realtek   299533  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
i915                  330089  3 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         32836  1 i915
uvcvideo               62379  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
eeepc_wmi               3571  0 
btusb                  12929  1 
sparse_keymap           3837  1 eeepc_wmi
drm                   206161  4 i915,drm_kms_helper
videodev               49359  1 uvcvideo
bluetooth              59213  8 rfcomm,sco,bnep,l2cap,btusb
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12646  1 videodev
psmouse                62080  0 
serio_raw               4910  0 
intel_agp              32080  2 i915
i2c_algo_bit            6208  1 i915
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
video                  22176  1 i915
output                  2527  1 video
parport                37032  3 parport_pc,ppdev,lp
ahci                   21857  0 
libahci                26167  2 ahci
atl1c                  34955  0




$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.




$ uname -mr
2.6.35-22-generic x86_64



Restarting the network: I did that and got the OK, but it didn't fix the problem.

---

