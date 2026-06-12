---
title: "Logitech Communicator STX wont work"
date: 2009-08-04
forum: Multimedia Software
---

### Post by mstjohn1974 on 2009-08-04
I just tried something else...usually I use Skype with my Webcam and it just crashed as soon as I turn on video but I downloaded cheese it is like Apples Photoboth App and that one works. So I dont know where now to look at.

I am having some trouble with my WebCam a Logitech Communicator STX. The System recognizes it and loads gspca driver but it wont work. I like to use Ubuntu but as long as I am not getting it working I stick with Debian Lenny. Funny that it works there but not on Ubuntu 9.04.

**This is the dmesg output:**
[ 1264.424090] usb 4-1: new full speed USB device using uhci_hcd and address 3
[ 1264.616736] usb 4-1: configuration #1 chosen from 1 choice
[ 1264.618177] gspca: probing 046d:08d7
[ 1266.252143] zc3xx: probe 2wr ov vga 0x0000
[ 1266.296105] zc3xx: probe sensor -> 11
[ 1266.296111] zc3xx: Find Sensor HV7131R(c)
[ 1266.301678] gspca: probe ok

**This is the lsusb output:**
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**This is the lsmod output:**
Module                  Size  Used by
snd_usb_audio          90528  1 
snd_usb_lib            24320  1 snd_usb_audio
snd_hwdep              15108  1 snd_usb_audio
gspca_zc3xx            55680  0 
gspca_main             29952  1 gspca_zc3xx
videodev               41600  1 gspca_main
v4l1_compat            21764  1 videodev
michael_mic            10496  2 
arc4                    9856  2 
ecb                    10752  2 
i915                   67844  2 
drm                    96424  3 i915
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
b44                    35984  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 18496  0 
ssb                    41220  1 b44
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 44748  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
mii                    13312  1 b44
intel_agp              34108  1 
ieee80211_crypt_tkip    16896  0 
snd                    62756  19 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
agpgart                42696  3 drm,intel_agp
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
dcdbas                 15264  0 
wl                   1281364  0 
pcspkr                 10496  0 
psmouse                61972  0 
serio_raw              13444  0 
ieee80211_crypt        13444  2 ieee80211_crypt_tkip,wl
video                  25360  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

**Here a Picture what happend when I start skype:**

[IMG]http://lh4.ggpht.com/_lMmtz-tvfjk/SnjnKWyOFAI/AAAAAAAADtg/2p0Kmk8UAVI/Untitled.png[/IMG]

Every help is greatly appreciated. Thanks in advanced.

---

### Post by yahs on 2009-08-23
Re: Logitech Webcam STX does not work in Jaunty 9.04
I have the same webcam

lsusb output

Bus 002 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX

This is a known bug. skype uses v4l1, Intrepid uses v4l2.
There are a number of postings on this topic but a quick fix which works for me is as follows.

open a terminal and type

LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so skype

You can test your webcam under v4l1 and v4l2 by running gstreamer-properties from a terminal

---

### Post by RedSingularity on 2009-08-23
Yep, i had the same problem with the same camera.  I got so fed up with it that i just returned the camera and got one that "just works".  The Quickcam Communicate MP.

---

### Post by tkrahn on 2009-11-16
Me too, I have the same problem. Any help would be appreciated.

---

### Post by tkrahn on 2009-11-16
This did the job for me! 
> open a terminal and type
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
Tnx [yahs]("http://ubuntuforums.org/member.php?u=646387")!

Thomas

---

### Post by mstjohn1974 on 2009-11-16
I couldn't get it to work so I ended up buying a new Webcam. I bought Logitech, Inc. QuickCam Communicate MP/S5500 and I can recommend this one. I also recommend alway buy a Webcam that is UVC Complaint. Look here [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) to get an Idea. This is real plug and play. I didn't need to do anything.

---

### Post by DeepSix on 2010-01-17
Unsure of the policy of resurrecting semi old posts in this forum, if this is frowned on or not allowed I apologize but this forum was relevant data in it related to the policy I had.

So I followed this tutorial trying to fix my cam which includes the "LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so skype" code in it, in a more efficient manner. [https://answers.launchpad.net/ubuntu/+question/49739]("https://answers.launchpad.net/ubuntu/+question/49739")

But I came across this thread and I tried in terminal rather then through that method and I got an error message:
```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```

Maybe someone could help me understand what this means?

---

