---
title: "WinTV usb2: no signal in tvtime"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by cbrewer on 2007-02-03
When I attempt to view the output of my WinTV usb2 external tuner with tvtime, all I see is a blue screen with the words 'no signal'. I've tested the tuner on Windows and it works fine there.

Both dmesg and lsmod seem to indicate that the appropriate drivers are loaded and running, and the text in the dmesg output also seems to indicate that it found the correct card. 
/dev/video0 exists as well.

Just for a quick test I plugged in an old webcam I had laying around... I was amazed when it fired right up, no hassles, and could be viewed through tvtime at /dev/video1. So at least SOMETHING works with usb and video on my hardware.

Oh, and I'm running Ubuntu 6.10, just installed today and freshly updated.

One minor thing that concerns me is that the driver announces that the tuner has support for a radio, when I'm pretty certain that it actually doesn't (that's a different model).

Does anyone have any ideas what might be wrong? I'm stumped.

Regards,
Chris

'dmesg' output excerpt:

[11875.909712] em28xx v4l2 driver version 0.0.1 loaded
[11875.910230] em28xx new video device (2040:4200): interface 0, class 255
[11875.910369] em28xx #0: Alternate settings: 8
[11875.910478] em28xx #0: Alternate setting 0, max size= 0
[11875.910481] em28xx #0: Alternate setting 1, max size= 1024
[11875.910484] em28xx #0: Alternate setting 2, max size= 1448
[11875.910487] em28xx #0: Alternate setting 3, max size= 2048
[11875.910490] em28xx #0: Alternate setting 4, max size= 2304
[11875.910492] em28xx #0: Alternate setting 5, max size= 2580
[11875.910495] em28xx #0: Alternate setting 6, max size= 2892
[11875.910498] em28xx #0: Alternate setting 7, max size= 3072
[11876.245402] tuner 0-0063: chip found @ 0xc6 (em28xx #0)
[11876.245900] tuner 0-0063: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[11876.251687] input: i2c IR (EM2840 Hauppauge) as /class/input/input11
[11876.252019] ir-kbd-i2c: i2c IR (EM2840 Hauppauge) detected at i2c-0/0-0030/ir0 [em28xx #0]
[11876.366505] msp3400 0-0044: MSP3445G-B8 found @ 0x88 (em28xx #0)
[11876.366510] msp3400 0-0044: MSP3445G-B8 supports radio, mode is autodetect and autoselect
[11876.408398] em28xx #0: i2c eeprom 00: 1a eb 67 95 40 20 00 42 20 00 44 03 82 18 6a 18
[11876.408410] em28xx #0: i2c eeprom 10: 00 00 24 57 6e 02 00 00 60 00 00 00 02 00 00 00
[11876.408419] em28xx #0: i2c eeprom 20: 1e 00 10 10 00 00 00 88 b8 00 00 00 00 00 00 00
[11876.408428] em28xx #0: i2c eeprom 30: 00 00 20 40 20 80 02 20 01 01 01 01 00 00 00 00
[11876.408437] em28xx #0: i2c eeprom 40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11876.408445] em28xx #0: i2c eeprom 50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[11876.408454] em28xx #0: i2c eeprom 60: 00 00 00 00 00 00 00 00 00 00 18 03 30 00 30 00
[11876.408462] em28xx #0: i2c eeprom 70: 31 00 30 00 35 00 30 00 32 00 31 00 30 00 36 00
[11876.408471] em28xx #0: i2c eeprom 80: 00 00 18 03 57 00 69 00 6e 00 54 00 56 00 20 00
[11876.408480] em28xx #0: i2c eeprom 90: 55 00 53 00 42 00 32 00 00 00 00 00 00 00 00 00
[11876.408488] em28xx #0: i2c eeprom a0: 84 12 00 00 05 50 1a 7f 08 70 23 1c a4 92 18 91
[11876.408497] em28xx #0: i2c eeprom b0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 da 3f
[11876.408506] em28xx #0: i2c eeprom c0: a0 00 74 02 01 0c 03 79 c4 00 00 00 00 00 00 00
[11876.408515] em28xx #0: i2c eeprom d0: 84 12 00 00 05 50 1a 7f 08 70 23 1c a4 92 18 91
[11876.408524] em28xx #0: i2c eeprom e0: ff 00 00 00 04 84 0a 00 01 01 20 77 00 40 da 3f
[11876.408533] em28xx #0: i2c eeprom f0: a0 00 74 02 01 0c 03 79 c4 00 00 00 00 00 00 00
[11876.408542] EEPROM ID= 0x9567eb1a
[11876.408544] Vendor/Product ID= 2040:4200
[11876.408547] I2S audio, sample rate=32k
[11876.408548] 500mA max power
[11876.408551] Table at 0x24, strings=0x1882, 0x186a, 0x0000
[11876.441583] tveeprom 0-0050: Hauppauge model 42012, rev D1B2, serial# 10502106
[11876.441590] tveeprom 0-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[11876.441593] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[11876.441597] tveeprom 0-0050: audio processor is MSP3445 (idx 12)
[11876.441600] tveeprom 0-0050: has radio
[11876.566775] tvp5150 0-005c: tvp5150am1 detected.
[11878.901187] em28xx #0: AC97 command still being executed: not handled properly!
[11879.174912] registered VBI
[11879.684668] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[11879.684674] em28xx #0: Found Hauppauge WinTV USB 2
[11879.685038] usbcore: registered new driver em28xx

 'lsmod' output:

Module                  Size  Used by
em28xx                 50728  0 
ovcamchip              22152  0 
w9968cf                74784  0 
msp3400                32928  0 
ir_kbd_i2c              9872  0 
snd_usb_audio          80416  0 
snd_usb_lib            18816  1 snd_usb_audio
snd_rawmidi            27264  1 snd_usb_lib
snd_seq_device          9868  1 snd_rawmidi
tda9887                18448  0 
tuner                  54828  0 
snd_hwdep              10756  1 snd_usb_audio
tvp5150                19472  0 
compat_ioctl32          2432  2 em28xx,w9968cf
v4l1_compat            15108  1 em28xx
v4l2_common            17280  3 em28xx,msp3400,tuner
ir_common              28548  2 em28xx,ir_kbd_i2c
videodev               10752  2 em28xx,w9968cf
tveeprom               16144  1 em28xx
i2c_core               23424  9 em28xx,ovcamchip,w9968cf,msp3400,ir_kbd_i2c,tda9887,tuner,tvp5150,tveeprom
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
apm                    23280  2 
i915                   21632  2 
drm                    74644  3 i915
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
lp                     12964  0 
af_packet              24584  4 
tsdev                   9152  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
e1000                 128452  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
e100                   38020  0 
mii                     6912  1 e100
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
psmouse                41352  0 
serio_raw               8452  0 
snd_pcm                84612  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
evdev                  11392  1 
floppy                 63044  0 
intel_agp              26012  1 
agpgart                34888  3 drm,intel_agp
pcspkr                  4352  0 
snd                    58372  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  7 em28xx,w9968cf,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 6276  0 
processor              31560  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by gmc on 2007-02-03
> **cbrewer said:**
> When I attempt to view the output of my WinTV usb2 external tuner with tvtime, all I see is a blue screen with the words 'no signal'. I've tested the tuner on Windows and it works fine there.

Both dmesg and lsmod seem to indicate that the appropriate drivers are loaded and running, and the text in the dmesg output also seems to indicate that it found the correct card. 
/dev/video0 exists as well.

Just for a quick test I plugged in an old webcam I had laying around... I was amazed when it fired right up, no hassles, and could be viewed through tvtime at /dev/video1. So at least SOMETHING works with usb and video on my hardware.

Oh, and I'm running Ubuntu 6.10, just installed today and freshly updated.

One minor thing that concerns me is that the driver announces that the tuner has support for a radio, when I'm pretty certain that it actually doesn't (that's a different model).

Does anyone have any ideas what might be wrong? I'm stumped.

Regards,
Chris


Chris, the WinTV USB2 only supports mpeg2 output and unfortunately TVTime does not. Try this ´vlc - < /dev/video1´ or ´mplayer - < /dev/video1´. As for radio support, I think you´ll find that it does. Check this mailing list for more information... **[http://www.isely.net/pipermail/pvrusb2/](http://www.isely.net/pipermail/pvrusb2/)**

Gord

---

### Post by cbrewer on 2007-02-03
Gord-

Thanks very much for your reply. Alas, vlc doesn't seem any happier. When I attempt to open /dev/video0 (which is my WinTV capture device; video1 is a webcam used for testing) vlc displays the message:

[00000289] v4l demuxer error: mmap unsupported

I'm confused, as others ([http://ubuntu.flowconsult.at/en/hauppauge-wintv-usb2/](http://ubuntu.flowconsult.at/en/hauppauge-wintv-usb2/)) don't seem to have any problems with this device at all.

Is there something else I'm overlooking?

Regards,
Chris

---

### Post by gmc on 2007-02-03
> **cbrewer said:**
> Gord-

Thanks very much for your reply. Alas, vlc doesn't seem any happier. When I attempt to open /dev/video0 (which is my WinTV capture device; video1 is a webcam used for testing) vlc displays the message:

[00000289] v4l demuxer error: mmap unsupported

I'm confused, as others ([http://ubuntu.flowconsult.at/en/hauppauge-wintv-usb2/](http://ubuntu.flowconsult.at/en/hauppauge-wintv-usb2/)) don't seem to have any problems with this device at all.

Is there something else I'm overlooking?

Regards,
Chris

I assume you´ve extracted the firmware files needed for the driver and put them in /usr/lib/firmware (that´s what caught me the first time). For more information check [here.]("http://www.isely.net/pvrusb2/pvrusb2.html") Mike Isely is the author of the pvrusb2 driver and is very helpful in diagnosing problems. You might want to sign up to the mailing list and ask there.

Gord

---

### Post by cbrewer on 2007-02-03
Gord-

AFAIK, the "WinTV usb2" does not require firmware- the page you're referring to is for the "WinTV **PVR** usb2", which is a completely different (and significantly more expensive) animal.

Alas, 'google' has come up dry on the problems I'm seeing (other than it should work, and that it apparently used to work under a previous release of Ubuntu).

I originally tried to get it working under Fedora Core 6. In that environment, tvtime was actually able to use it (!!) but it failed under vlc with the aforementioned 'mmap unsupported' message. I was hoping to sidestep having to download the kernel source/recompile/diagnose the driver issue by trying another contemporary Linux distribution.

I'm guessing that either the em28xx driver was ever-so-lightly modified for some other device (causing issues for this one) or that Hauppauge is now shipping a modified revision of the original product, or there's something unique about my system that causes it to not work. I'll try posting in the Video for Linux em28xx forum(s) and see what they say.

I really appreciate your time in responding to my requests. If you (or anyone else) have any other suggestions, I'd be very glad to hear them, but otherwise I guess I'm going to have to roll my sleeves up and start digging into the code. Or spring for another video capture card :( 

Regards,

Chris

---

### Post by anaconda on 2007-02-20
Actually wintv nova-t usb2 does need firmware copied to /lib/firmware directory..

read this thread for more info:
[http://www.ubuntuforums.org/showthread.php?t=274014&highlight=wintv](http://www.ubuntuforums.org/showthread.php?t=274014&highlight=wintv)

---

### Post by hunteramor on 2007-03-06
you're getting farther than i am at least, this is what i get from dmesg:

[ 1043.017502] em28xx #0: reading i2c device failed (error=-71)
[ 1043.121489] em28xx #0: reading i2c device failed (error=-71)
[ 1043.225478] em28xx #0: reading i2c device failed (error=-71)
[ 1043.329460] em28xx #0: reading i2c device failed (error=-71)
[ 1043.429447] em28xx #0: reading i2c device failed (error=-71)
[ 1043.529434] em28xx #0: reading i2c device failed (error=-71)
[ 1043.629421] em28xx #0: reading i2c device failed (error=-71)
[ 1043.729402] em28xx #0: reading i2c device failed (error=-71)
[ 1043.829520] em28xx #0: reading i2c device failed (error=-71)
[ 1043.933506] em28xx #0: reading i2c device failed (error=-71)
[ 1044.037490] em28xx #0: reading i2c device failed (error=-71)
[ 1044.141478] em28xx #0: reading i2c device failed (error=-71)
[ 1044.245464] em28xx #0: reading i2c device failed (error=-71)
[ 1044.349480] em28xx #0: reading i2c device failed (error=-71)
[ 1044.453438] em28xx #0: reading i2c device failed (error=-71)
[ 1044.557426] em28xx #0: reading i2c device failed (error=-71)

i just upgraded to feisty to get the latest kernel, which i understood included drivers for wintv-usb2 but so far it's not helping me get any farther than i was with edgy...

---

### Post by hunteramor on 2007-03-06
alright, i was able to fix that problem.  dmesg output now looks right.  when i try to use tvtime, however, i get a blue screen with the message "Message too long. Cannot open capture device /dev/video0" in the bottom left

If I try to use vlc or mplayer, I get a similar message: bash: /dev/video0: Message too long

Any ideas?

---

### Post by dems on 2007-05-01
Im having a problem also since upgrade from edgy to feisty... If i boot using 2.6.17-11-generic my tv card works perfectly, but if i choose latest 2.6.20-15-generic kernel it seems like the device is correctly detected and the em28xx module is loaded but i have not images at all (as i there was no video connected to it ...)

---

