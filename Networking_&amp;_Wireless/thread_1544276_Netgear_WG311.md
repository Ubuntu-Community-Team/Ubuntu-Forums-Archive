---
title: "Netgear WG311"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by Wotan87 on 2010-08-02
hello 
I have a Netgear WG111V3 
it works natively on my kubuntu 10.04 64 bit
However I can't connect with a bitrate higer than 1M
  at 11M Knetworkmanager say "connected" but no way to load an internet page
  at 54M it say "configuring interface" then "getting network address" and never get "connected"

What should I do?

---

### Post by Wotan87 on 2010-08-02
I just tried ndiswrapper to see if it get better with the windows driver but:
```

max@max:~$ sudo modprobe -r rtl8187  prism2_usb  r8187b islsm_usb islsm islsm_pci
[sudo] password for max: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module r8187b not found.

max@max:~$ cd /home/max/WG111

max@max:~/WG111$ ndiswrapper -l
net111v2 : driver installed

max@max:~/WG111$ sudo ndiswrapper -r net111v2


max@max:~/WG111$ sudo ndiswrapper -i WG111v3.inf
installing wg111v3 ...

max@max:~/WG111$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg111v3 : driver installed
        device (0846:4260) present (alternate driver: rtl8187)

max@max:~/WG111$ ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
module configuration already contains alias directive
                                                                                                                                                                                                                                          
max@max:~/WG111$ sudo modprobe ndiswrapper                                                                                                                                                                 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. 
                                                                                                
max@max:~/WG111$ iwconfig                                                                                                                                                                                  
lo        no wireless extensions.                                                                                                                                                                          
                                                                                                                                                                                                           
eth0      no wireless extensions.                                                                                                                                                                          

max@max:~/WG111$ lsmod
Module                  Size  Used by
ndiswrapper           244768  0 
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25677  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87882  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_seq_oss            31219  0 
vga16fb                12757  0 
arc4                    1473  0 
snd_seq_midi            5829  0 
vgastate                9857  1 vga16fb
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               515227  2 
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    60847  1 nouveau
uvcvideo               62467  0 
videodev               40518  1 uvcvideo
ppdev                   6375  0 
drm_kms_helper         30742  1 nouveau
snd                    71106  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            15495  2 uvcvideo,videodev
edac_core              45423  0 
i2c_nforce2             6099  0 
k8temp                  3912  0 
edac_mce_amd            9278  0 
asus_atk0110           10033  0 
joydev                 11072  0 
parport_pc             29958  1 
psmouse                64576  0 
drm                   199204  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    12020  1 videodev
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41084  0 
hid                    83440  1 usbhid
ohci1394               30260  0 
ieee1394               94771  1 ohci1394
pata_amd               11962  0 
sata_nv                23778  2 
forcedeth              55592  0 


```
What Should I do?

---

### Post by Wotan87 on 2010-08-02
up ?

---

### Post by Wotan87 on 2010-08-03
re-up

---

