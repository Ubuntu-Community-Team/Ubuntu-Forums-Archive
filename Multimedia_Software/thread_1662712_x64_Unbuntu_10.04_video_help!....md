---
title: "x64 Unbuntu 10.04 video help!..."
date: 2011-01-08
forum: Multimedia Software
---

### Post by VcDeveloper on 2011-01-08
How do you get the video working for the x64 10.04? Can anyone link me to a post of someone who has successfully got this working or do I have to use the 32?

I'm trying to setup a streaming server for live broadcasts.  For starters, I'm having no success with Cheese indicating no Device found.  Looking in the /dev folder and I don't see it.

---

### Post by BicyclerBoy on 2011-01-08
You don't mean video.

You are trying to stream or capture (say Cheese) from a webcam ?

Webcam support is always being added.
What is your webcam ?

lsusb

Support comes from video4linux & guvcview (UVC) projects.

Both websites list supported devices.

Video4linux is in the kernel. To get later v4l v4l2 modules the easiest way is upgrade to 10.10 & later kernel (maybe kernel ppa).

guvcview is in the *buntu repos..

Try guvcview first.
Search LinuxTV v4l & guvcview for your device..

---

### Post by VcDeveloper on 2011-01-08
> **BicyclerBoy said:**
> You don't mean video. Oh yea, thats correct!

> **BicyclerBoy said:**
>  You are trying to stream or capture (say Cheese) from a webcam ? just was using it to test to see if was working.

> **BicyclerBoy said:**
> Webcam support is always being added.
What is your webcam ? Right now, I have a Logitech Quick Cam, but looking into  purchasing MS 7ND-00001 LifeCam HD-5000 Webcam or LifeCam Cenema Webcam

 > **BicyclerBoy said:**
> lsusb 
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 018: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 006 Device 002: ID 0557:8021 ATEN International Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Didn't have my web cam plugged in, but I did before and it did detect it...

> **BicyclerBoy said:**
>  Support comes from video4linux & guvcview (UVC) projects.

Both websites list supported devices.

Video4linux is in the kernel. To get later v4l v4l2 modules the easiest way is upgrade to 10.10 & later kernel (maybe kernel ppa).

guvcview is in the *buntu repos..

Try guvcview first.
Search LinuxTV v4l & guvcview for your device.. Ok, I will upgrad to 10.10

---

### Post by BicyclerBoy on 2011-01-08
Upgrading to 10.10 was just a suggestion...

It may be a lot of hassle for no gain if there is no support in 10.10..

Need to plug in webcam & then

lsusb

Need to know the USB id codes to be sure what it is..

But please try guvcview from the std ubuntu repos..

---

### Post by VcDeveloper on 2011-01-09
> **BicyclerBoy said:**
> Upgrading to 10.10 was just a suggestion...

It may be a lot of hassle for no gain if there is no support in 10.10..

Need to plug in webcam & then

lsusb

Need to know the USB id codes to be sure what it is..

But please try guvcview from the std ubuntu repos..

kern.log after plugging in
```
Jan  9 20:46:16 anointed kernel: [630260.267689] Linux video capture interface: v2.00
Jan  9 20:46:16 anointed kernel: [630260.270437] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
Jan  9 20:46:16 anointed kernel: [630260.280464] usbcore: registered new interface driver snd-usb-audio
Jan  9 20:46:16 anointed kernel: [630260.280473] usb 8-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x046D:0x08AE)
Jan  9 20:46:16 anointed kernel: [630260.363095] usb 8-2: PAS202BCB image sensor detected
Jan  9 20:46:17 anointed kernel: [630260.844090] usb 8-2: Initialization succeeded
Jan  9 20:46:17 anointed kernel: [630260.844170] usb 8-2: V4L2 device registered as /dev/video0
Jan  9 20:46:17 anointed kernel: [630260.844197] usbcore: registered new interface driver zc0301
```lsusb```

Bus 008 Device 002: ID 046d:08ae Logitech, Inc. QuickCam for Notebooks
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 026: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 003: ID 045e:00dd Microsoft Corp. 
Bus 006 Device 002: ID 0557:8021 ATEN International Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Uhmmmm.... Cheese is working now!.....  I had a couple of updates since the last testing of Cheese..

---

### Post by VcDeveloper on 2011-01-13
The mic on my webcam doesn't work.  In testing the video and sound with flumotion or media system selector I get a loud disturbing sound.  Does this mean I need a separate dedicated mic?

---

### Post by VcDeveloper on 2011-01-13
> **VcDeveloper said:**
> The mic on my webcam doesn't work.  In testing the video and sound with flumotion or media system selector I get a loud disturbing sound.  Does this mean I need a separate dedicated mic?

Well actully, I have flumotion 0.8 running and the mic is working...... Qualifty not there until, but  good for testing and configuring flumotion and Web Cam Studio for now..

---

### Post by BicyclerBoy on 2011-01-13
I did suggest guvcview...

It works so much better than processed sliced cheese..

It works nice on a netbook.

---

### Post by VcDeveloper on 2011-01-14
> **BicyclerBoy said:**
> I did suggest guvcview...

It works so much better than processed sliced cheese..

It works nice on a netbook.

Yes you did..., about to install it now, but I get a authentication warning, is this ok?

---

### Post by BicyclerBoy on 2011-01-14
Don't know..
Never happened on my computers.

It could be because of dependencies pulling in stuff from other repositories you do not have setup in apt/synaptic.
Like GTK or libavcodec52  ?

---

### Post by VcDeveloper on 2011-01-15
Yes, that was it!  I was following this tutorial **[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") and it had me enable "Unsupported updates".  When I disabled it, I no longer get the warning message.

---

### Post by VcDeveloper on 2011-01-15
I get this error: Unable to start with minimum setup - please reconnect your camera.  How and where is the setup preferences?

---

### Post by BicyclerBoy on 2011-01-15
Ridiculous as it sounds, you need the webcam plugged in before the program will launch.

Maybe able to force it to load from terminal command.

Once it is running the config settings screen is obvious except on netbook unity desktop where it tries to hide itself..

---

### Post by VcDeveloper on 2011-01-16
> **BicyclerBoy said:**
> Ridiculous as it sounds, you need the webcam plugged in before the program will launch.


I do have it plugged in, does this util work with usb webcams?

---

### Post by BicyclerBoy on 2011-01-16
Yes guvcview works with USB webcams & any other supported video4linux device..

Just because your webcam is identified by lspci does not mean it has loaded any driver for it.

Can look in output from
lsmod

Unplug the webcam.
Re plug webcam
In a terminal type
dmesg
post the last 10 lines..

We can search thru' lsmod maybe..

Other options:
*buntu 10.10 is looking like a better option or
You can install a later kernel from ubuntu kernel team ppa..

---

### Post by BicyclerBoy on 2011-01-16
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

[http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/](http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/)

The answer was on the ubuntu website..
Your webcam only works with *buntu 10.04 v4l & not v4l2.

Try in terminal..
*export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; guvcview*

You can change the menu launcher if this works..

---

### Post by VcDeveloper on 2011-01-17
> **BicyclerBoy said:**
> Yes guvcview works with USB webcams & any other supported video4linux device..

Can look in output from
lsmod

Unplug the webcam.
Re plug webcam
In a terminal type
dmesg
post the last 10 lines..

We can search thru' lsmod maybe..


----- lsmod ------
```
Module                  Size  Used by
webcamstudio            9589  0 
zc0301                 48778  0 
videodev               40518  2 webcamstudio,zc0301
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    11892  1 videodev
snd_usb_audio          92747  1 
snd_usb_lib            19193  1 snd_usb_audio
isofs                  33399  0 
udf                    85529  0 
crc_itu_t               1715  1 udf
nf_conntrack_ipv4      12980  2 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
xt_state                1490  2 
nf_conntrack           73966  2 nf_conntrack_ipv4,xt_state
xt_mark                 1055  4 
xt_NFQUEUE              2344  2 
xt_iprange              1645  2 
xt_tcpudp               2667  7 
ipt_REJECT              2384  2 
nfnetlink_queue         8205  2 
nfnetlink               4142  3 nfnetlink_queue
binfmt_misc             7960  1 
ppdev                   6375  0 
iptable_filter          2791  1 
ip_tables              18390  1 iptable_filter
snd_hda_codec_realtek   279008  1 
x_tables               22461  7 xt_state,xt_mark,xt_NFQUEUE,xt_iprange,xt_tcpudp,ipt_REJECT,ip_tables
snd_hda_intel          25741  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71251  19 snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64576  0 
nvidia              10832442  38 
vga16fb                12757  1 
soundcore               8052  1 snd
vgastate                9857  1 vga16fb
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
serio_raw               4918  0 
intel_agp              29319  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
joydev                 11104  0 
usbhid                 41116  0 
hid                    83472  1 usbhid
ohci1394               30260  0 
pata_jmicron            2747  0 
tulip                  50464  0 
ieee1394               94771  1 ohci1394
e1000e                136269  0 

```


----- dmesg ------
```
[1308733.540168] usb 8-2: USB disconnect, address 4
[1308733.540225] usb 8-2: Disconnecting ZC0301[P] PC Camera...
[1308733.540227] usb 8-2: V4L2 device /dev/video0 deregistered
[1308739.100111] usb 8-2: new full speed USB device using uhci_hcd and address 5
[1308739.308470] usb 8-2: configuration #1 chosen from 1 choice
[1308739.311699] usb 8-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x046D:0x08AE)
[1308739.373370] usb 8-2: PAS202BCB image sensor detected
[1308739.843370] usb 8-2: Initialization succeeded
[1308739.843459] usb 8-2: V4L2 device registered as /dev/video0

```

will be back with the results - *export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; guvcview*

---

### Post by VcDeveloper on 2011-01-17
> **BicyclerBoy said:**
> [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

[http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/](http://gurrier.wordpress.com/2010/05/30/problem-with-running-logitech-webcam-working-in-skype-on-ubuntu-10-04-lucid-lynx/)

The answer was on the ubuntu website..
Your webcam only works with *buntu 10.04 v4l & not v4l2.

Try in terminal..
*export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so; guvcview*

You can change the menu launcher if this works..

Here is the results of trying the export....
```
guvcview 1.1.3
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
/dev/video0 - device 1
/dev/video1 - device 2
reading link '/sys/class/video4linux/video1/device' failed: Failed to read the symbolic link '/sys/class/video4linux/video1/device': No such file or directory
Init. ZC0301[P] PC Camera (location: usb-0000:00:1d.2-2)
{ pixelformat = 'JPEG', description = 'JPEG' }
{ discrete: width = 0, height = 0 }
    Time interval between frame: 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 0, height = 0 }
    Time interval between frame: 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 0, height = 0 }
    Time interval between frame: 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 0, height = 0 }
    Time interval between frame: 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 0, height = 0 }
    Time interval between frame: 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 
checking format: 1196444237
Format unavailable: 1196444237.
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
ERROR: Minimum Setup Failed.
 Exiting...
Terminated.

```

Looks like I have to get one of the higher end models.  Need one anyway to get the best quality for streaming live.  I want to get a MS Webcam, but need to check if there supported and which one.

---

### Post by BicyclerBoy on 2011-01-17
Don't know what the error messages really mean but it did not work.
Forrest had the right idea..just keep running.

Don't know what to try now that is easy..

The only things left to try is download & build both video4linux & gspca...
This is not an minor undertaking & it could be a waste of effort.

Far easier to upgrade to Ubuntu10.10 & kernel & hope.

Give up & buy a webcam that works, give the old one to a windoze friend.

---

### Post by VcDeveloper on 2011-01-17
> **BicyclerBoy said:**
> 
Give up & buy a webcam that works, give the old one to a windoze friend.

Yea, thats what I'm going to do...., either I will go with..

[LIST]
[*]v9.10 (Karmic Koala) using Microsoft LifeCam Cinema or
[*]stay with 10.04 (Lucid) using one of these
a) Logitech Webcam C250
b) Logitech Webcam C500
c) Logitech Webcam C905

have to look at the spec's to see which one is the best.

[/LIST]

---

### Post by VcDeveloper on 2011-01-19
...and thanks for your help!  I really appreciate that!

---

