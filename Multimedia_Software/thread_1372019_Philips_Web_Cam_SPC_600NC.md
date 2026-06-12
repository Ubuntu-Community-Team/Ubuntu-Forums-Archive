---
title: "Philips Web Cam SPC 600NC"
date: 2010-01-04
forum: Multimedia Software
---

### Post by chessnerd on 2010-01-04
I am trying to get this old web cam to work on my desktop, which is running Xubuntu 9.04 with LXDE. I've read several posts about these kinds of web cams on several different forums, but nothing I found was good (ie everyone failed to get them to work under Linux) but the posts were a couple years old so I'm hopeful that the situation may have changed.

The computer does seem to realize that the device is attached. The light on the camera comes on (which under Windows means that it is recording) and when I check lsusb it give the full name of the camera, so it recognizes what kind of camera it is, but I can't get it to work under Camorama, Cheese, or Skype. All of them fail to see that a device is attached.

Is there some extra step I need to perform to get the computer to use the camera? If not, has anyone had any success with this web cam or a similar model?

---

### Post by chessnerd on 2010-01-05
Still no luck. 

I looked at [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) but it didn't help. I tried to install EasyCam as the page suggested, but it looks like Jaunty and EasyCam have irreconcilable dependency issues. (Personally, I think that Jaunty's father never hugged it enough as a child and that the passing of EasyCam's mother left a permanent scar on it.)

Maybe the joke will warrant a response?

Here are the last few lines of dmesg:
```
[ 1455.176028] usb 1-2: new full speed USB device using uhci_hcd and address 3
[ 1455.350714] usb 1-2: configuration #1 chosen from 1 choice
[ 1455.559041] Linux video capture interface: v2.00
[ 1455.566117] usbcore: registered new interface driver snd-usb-audio
[ 1455.577256] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[ 1455.595408] usb 1-2: SN9C105 PC Camera Controller detected (vid:pid 0x0471:0x0327)
[ 1455.773357] usb 1-2: No supported image sensor detected for this bridge
[ 1455.773485] usbcore: registered new interface driver sn9c102
```

---

### Post by chessnerd on 2010-01-07
I would prefer if this didn't become one of those dead threads that shows up when people who own the same webcam search for help with it in Linux, so I will keep pressing on.

If it is that I am missing info, please tell me what else I need to provide.

If it is that my cause is hopeless, tell me that. At this point I expect it is hopeless, as I know of nothing else to try...

---

### Post by Kivech on 2010-01-31
Yep, got the same problem here. I have the SPC700NC, but the whole thing is the same.

I tried a few things already, installing cheese didn't work, nor did some other cam software. In Skype the light just comes up for two secs when testing it, and then it dies out again.

I know there used to be a Linux driver set for these webcams, but I cannot remember for the life of me where to find them. Philips doesn't do them anymore, but some guy who used to work there continued to do the Linux drivers in his spare time. These even came with the caption tool that usually comes with these webcams.

Anyone has any idea where to find these or a substitute?

---

### Post by slakov on 2011-05-04
Hi all,

my Philips SPC 600 NC drives me crazy. It didn't work in 9.10 then it worked in 10.04 and it stopped working again after update to 11.04. Anybody has a slightest idea of what a $%# is going on? 


[78978.680016] usb 4-2: new full speed USB device using uhci_hcd and address 9
[78978.841264] gspca: probing 0471:0327
[78978.846223] sonixj: Sonix chip id: 11
[78978.889221] sonixj: Unknown sensor 0000 - forced to mi0360
[78978.891285] input: sonixj as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/input/input12
[78978.891386] gspca: video0 created

---

### Post by no2498 on 2011-05-04
open a terminal type dmesg click enter
after it stops type lsusb click enter did it find the sensor
use to be a package for the phillips cam's in the package manager
just look for webcam it use to come up that way

in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

try the cam in cheese

---

### Post by slakov on 2011-05-10
> **no2498 said:**
> open a terminal type dmesg click enter
after it stops type lsusb click enter did it find the sensor
use to be a package for the phillips cam's in the package manager
just look for webcam it use to come up that way

in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

try the cam in cheese


thanks for the reply. 

the output of dmesg is

[ 4758.200019] usb 4-2: new full speed USB device using uhci_hcd and address 2
[ 4758.472812] Linux video capture interface: v2.00
[ 4758.496574] gspca: v2.12.0 registered
[ 4758.501934] gspca: probing 0471:0327
[ 4758.506030] sonixj: Sonix chip id: 11
[ 4758.550032] sonixj: Unknown sensor 0000 - forced to mi0360
[ 4758.552100] input: sonixj as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/input/input5
[ 4758.552210] gspca: video0 created
[ 4758.552247] usbcore: registered new interface driver sonixj
[ 4758.624299] usbcore: registered new interface driver snd-usb-audio


and lsusb 

Bus 004 Device 002: ID 0471:0327 Philips (or NXP) Webcam SPC 6000 NC (Webcam w/ mic)

Playing with gstremar-properties doesn't help.

Any ideas?

---

### Post by no2498 on 2011-05-10
install xawtv it loads a cam grabber
try xawtv and cheese

---

### Post by slakov on 2011-05-10
> **no2498 said:**
> install xawtv it loads a cam grabber
try xawtv and cheese

thank you for the reply. Cheese shows black screen, also camera indicator turns on. Xawtv also doesn't work, here is the message it spits before the black screen:

This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.38-8-generic-pae)
xinerama 0: 1440x900+0+0
xinerama 1: 1440x900+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x100000001 [PAL_B,(null)]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
v4l2: oops: select timeout
libv4l2: error dequeuing buf: Input/output error
v4l2: read: Input/output error


Many thanks upfront!

---

### Post by no2498 on 2011-05-10
? did you install the philips cam package

---

### Post by slakov on 2011-05-10
> **no2498 said:**
> ? did you install the philips cam package

yes, I've installed phillips cam package - setpwc. As far as I can see it only controls, brightness, compression, sharpness and things like that. Still no luck with the webcam.

---

### Post by no2498 on 2011-05-10
type this in a terminal lsmod click enter

---

### Post by slakov on 2011-05-10
> **no2498 said:**
> type this in a terminal lsmod click enter

here it is:

Module                  Size  Used by
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
snd_hda_codec_analog    75442  1 
snd_hda_intel          24140  2 
snd_usb_audio          91410  1 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
snd_pcm                80244  3 snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  17 snd_hda_codec_analog,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
i915                  450979  2 
gspca_sonixj           32443  0 
gspca_main             27894  1 gspca_sonixj
drm_kms_helper         40745  1 i915
drm                   184133  3 i915,drm_kms_helper
videodev               75143  1 gspca_main
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
dcdbas                 14054  0 
lp                     13349  0 
ppdev                  12849  0 
psmouse                59039  0 
parport_pc             32111  1 
parport                36746  3 lp,ppdev,parport_pc
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
joydev                 17322  0 
video                  18951  1 i915
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
e1000e                138627  0 
libahci                25548  1 ahci

---

### Post by no2498 on 2011-05-10
this is the lind i do not see in yours

v4l1_compat            13251  1 videodev

you need a v4l to convert so v4l2 file

they did away with v4l and went to v4l2

after you install the v4l2 file 


in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

### Post by slakov on 2011-05-10
> **no2498 said:**
> this is the lind i do not see in yours

v4l1_compat            13251  1 videodev

you need a v4l to convert so v4l2 file

they did away with v4l and went to v4l2

after you install the v4l2 file 


in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam



I have only v4l2 available in gstreamer-properties. When I try from terminal
v4l-conf

the output is:

v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1440x900, depth=24, bpp=32, bpl=5760, base=unknown
/dev/video0 [v4l2]: no overlay support

---

### Post by no2498 on 2011-05-10
this is mine 
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=0xf0000000
/dev/video0 [v4l2]: no overlay support


for gstreamer you need good,bad,ugly and 10 for the ubuntu/linux you use

---

### Post by slakov on 2011-05-11
> **no2498 said:**
> this is mine 
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1024x768, depth=24, bpp=32, bpl=4096, base=0xf0000000
/dev/video0 [v4l2]: no overlay support


for gstreamer you need good,bad,ugly and 10 for the ubuntu/linux you use


thanks! do you have any idea about how to make v4l to appear in gstreamer-properties?

---

### Post by no2498 on 2011-05-11
no i do not
you can find them in the package manager
did you get the compat /convert file for v4l


Collection of video4linux support libraries

libv4l is a collection of libraries which adds a thin abstraction layer on
top of video4linux2 devices. The purpose of this (thin) layer is to make it
easy for application writers to support a wide variety of devices without
having to write separate code for different devices in the same class. libv4l
consists of 3 different libraries: libv4lconvert, libv4l1 and libv4l2.

libv4lconvert offers functions to convert from any (known) pixelformat
to BGR24, RGB24, YUV420 and YVU420.

libv4l1 offers the (deprecated) v4l1 API on top of v4l2 devices, independent
of the drivers for those devices supporting v4l1 compatibility (which many
v4l2 drivers do not).

libv4l2 offers the v4l2 API on top of v4l2 devices, while adding for the
application transparent libv4lconvert conversion where necessary.

This package contains the shared libraries.


see if you can find this 1

---

### Post by slakov on 2011-05-12
> **no2498 said:**
> no i do not
you can find them in the package manager
did you get the compat /convert file for v4l


Collection of video4linux support libraries

libv4l is a collection of libraries which adds a thin abstraction layer on
top of video4linux2 devices. The purpose of this (thin) layer is to make it
easy for application writers to support a wide variety of devices without
having to write separate code for different devices in the same class. libv4l
consists of 3 different libraries: libv4lconvert, libv4l1 and libv4l2.

libv4lconvert offers functions to convert from any (known) pixelformat
to BGR24, RGB24, YUV420 and YVU420.

libv4l1 offers the (deprecated) v4l1 API on top of v4l2 devices, independent
of the drivers for those devices supporting v4l1 compatibility (which many
v4l2 drivers do not).

libv4l2 offers the v4l2 API on top of v4l2 devices, while adding for the
application transparent libv4lconvert conversion where necessary.

This package contains the shared libraries.


see if you can find this 1


I can not find  compat /convert file for v4l in repositories. Perhaps it's really deprecated by now.

---

### Post by no2498 on 2011-05-12
libv4l-0
Collection of video4linux support libraries

thats the name of it

---

### Post by Kivech on 2011-05-12
Hi guys,

I was following this thread for a while, and also posted in here almost a year ago. 

I still haven't managed to solve my webcam issue either. I followed all the suggested steps here, but unfortunately nothing works.

See, like I suggested in my post early on in this thread:
The driver is not maintained anymore for quite some time now. Some versions back in Ubuntu it used to work out of the box, but then, for some reason, they discontinued support of the driver.
Mostly because the one who maintained it, stopped doing so (some ex-Philips employee who did it in his spare time for a while).

I'm quite stumped that we don't have a decent alternative, because where I live (in Italy) you find these webcams all over the place. I actually have two models of them the 700 and the 600.

It makes me believe that in some way Philips did something 'special' with their hardware which doesn't allow us to configure them in a simple fasion.

Now I am completely ignorant in this matter, but it is not like there is a way in which we can use the Windows drivers? Those are still maintained.
Meanwhile I will see if I can get something from Philips support. It's a long shot, but who knows.

I'll keep following your progress and in case I hear anything new, I will make sure to let you guys know.

---

### Post by Kivech on 2011-05-12
Well, just got my confirmation from Philips customer support of my submitted ticket.

I will keep you guys posted on the progress.

---

### Post by Kivech on 2011-05-13
Reply from Philips customer support is (in short):
"Webcam is too old, so we will not make linux drivers for it."

However, it seems that someone else is, and that web site can be found here:

[http://saillard.org/linux/pwc/]("http://saillard.org/linux/pwc/")

I cannot try it out today, but please have a look at it and see if it is useful (even if it is for the 900 model).

Good luck.

---

### Post by slakov on 2011-05-13
> **no2498 said:**
> libv4l-0
Collection of video4linux support libraries

thats the name of it

yes, libv4l-0 is installed, but id doesn't appear in gstreamer properties. I can choose Custom plugin but then it asks for the pipeline which is v4l2src for libv4l2, I don't know how to use libv4l instead (v4lsrc doesn't work)

---

### Post by patmagee1024 on 2011-05-13
Here's a dump of my system. I have the 900NC and it works thru VLC. I don't use it as a webcam but it works flawlessly.

dmesg
[   19.992717] pwc: Philips webcam module version 10.0.13 loaded.
[   19.992719] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   19.992720] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   19.992722] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   19.992740] pwc: Philips SPC 900NC USB webcam detected.
[   20.015165] pwc: Registered as /dev/video0.

lsmod
Module                  Size  Used by
aic79xx               154147  0 
auth_rpcgss            44452  2 nfsd,nfs
binfmt_misc             7960  1 
bitblit                 5811  1 fbcon
coretemp                5505  0 
dcdbas                  6886  0 
dell_wmi                2177  0 
e1000e                136269  0 
exportfs                4202  1 nfsd
fbcon                  39270  71 
fglrx                2353486  33 
font                    8053  1 fbcon
hid                    83600  1 usbhid
hwmon_vid               3130  1 it87
ieee1394               94771  1 ohci1394
it87                   24460  0 
joydev                 11104  0 
lockd                  75079  2 nfsd,nfs
lp                      9336  0 
nfs                   310867  0 
nfs_acl                 2709  2 nfsd,nfs
nfsd                  304374  13 
ohci1394               30260  0 
parport                37160  3 parport_pc,ppdev,lp
parport_pc             29958  0 
ppdev                   6375  0 
psmouse                64576  0 
pwc                    83150  1 
scsi_transport_spi     26284  1 aic79xx
serio_raw               4918  0 
shpchp                 33711  0 
snd                    71251  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279072  1 
snd_hda_intel          25805  2 
snd_hwdep               6924  2 snd_hda_codec,snd_usb_audio
snd_mixer_oss          16299  1 snd_pcm_oss
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_pcm_oss            41394  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_dummy           1782  0 
snd_seq_midi            5829  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq_oss            31191  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_usb_audio          92747  1 
snd_usb_lib            19193  1 snd_usb_audio
softcursor              1565  1 bitblit
soundcore               8052  1 snd
sunrpc                228035  12 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
tileblit                2487  1 fbcon
usbhid                 41116  0 
usb_storage            50377  0 
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    11892  1 videodev
vga16fb                12757  1 
vgastate                9857  1 vga16fb
videodev               40518  2 pwc
vmci                   55037  0 
vmmon                  75759  0 
vmnet                  44168  3 

Command line to activate it
vlc --aspect-ratio 4:3 --width 400 --qt-display-mode 2 v4l2:// :v4l-vdev="/dev/video0"


If you want other info about my config let me know.

---

### Post by slakov on 2011-05-13
> **patmagee1024 said:**
> Here's a dump of my system. I have the 900NC and it works thru VLC. I don't use it as a webcam but it works flawlessly.

dmesg
[   19.992717] pwc: Philips webcam module version 10.0.13 loaded.
[   19.992719] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   19.992720] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   19.992722] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   19.992740] pwc: Philips SPC 900NC USB webcam detected.
[   20.015165] pwc: Registered as /dev/video0.

lsmod
Module                  Size  Used by
aic79xx               154147  0 
auth_rpcgss            44452  2 nfsd,nfs
binfmt_misc             7960  1 
bitblit                 5811  1 fbcon
coretemp                5505  0 
dcdbas                  6886  0 
dell_wmi                2177  0 
e1000e                136269  0 
exportfs                4202  1 nfsd
fbcon                  39270  71 
fglrx                2353486  33 
font                    8053  1 fbcon
hid                    83600  1 usbhid
hwmon_vid               3130  1 it87
ieee1394               94771  1 ohci1394
it87                   24460  0 
joydev                 11104  0 
lockd                  75079  2 nfsd,nfs
lp                      9336  0 
nfs                   310867  0 
nfs_acl                 2709  2 nfsd,nfs
nfsd                  304374  13 
ohci1394               30260  0 
parport                37160  3 parport_pc,ppdev,lp
parport_pc             29958  0 
ppdev                   6375  0 
psmouse                64576  0 
pwc                    83150  1 
scsi_transport_spi     26284  1 aic79xx
serio_raw               4918  0 
shpchp                 33711  0 
snd                    71251  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279072  1 
snd_hda_intel          25805  2 
snd_hwdep               6924  2 snd_hda_codec,snd_usb_audio
snd_mixer_oss          16299  1 snd_pcm_oss
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_oss
snd_pcm_oss            41394  0 
snd_rawmidi            23420  2 snd_usb_lib,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_dummy           1782  0 
snd_seq_midi            5829  0 
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq_oss            31191  0 
snd_timer              23649  2 snd_pcm,snd_seq
snd_usb_audio          92747  1 
snd_usb_lib            19193  1 snd_usb_audio
softcursor              1565  1 bitblit
soundcore               8052  1 snd
sunrpc                228035  12 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
tileblit                2487  1 fbcon
usbhid                 41116  0 
usb_storage            50377  0 
v4l1_compat            15495  1 videodev
v4l2_compat_ioctl32    11892  1 videodev
vga16fb                12757  1 
vgastate                9857  1 vga16fb
videodev               40518  2 pwc
vmci                   55037  0 
vmmon                  75759  0 
vmnet                  44168  3 

Command line to activate it
vlc --aspect-ratio 4:3 --width 400 --qt-display-mode 2 v4l2:// :v4l-vdev="/dev/video0"


If you want other info about my config let me know.

thanks for the reply! In my case vlc behaves like other camera capture programs - turn on the indicator on the camera but the screen stays blank.

---

### Post by patmagee1024 on 2011-05-13
I found a couple of other items in dmesg.

[   19.992717] pwc: Philips webcam module version 10.0.13 loaded.
[   19.992719] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   19.992720] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   19.992722] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   19.992740] pwc: Philips SPC 900NC USB webcam detected.
[   20.015165] pwc: Registered as /dev/video0.
[   20.018157] input: PWC snapshot button as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/input/input3
[   20.018212] usbcore: registered new interface driver Philips webcam

I had this device working under 9.10 before I reloaded to 10.04. Also, I did a scratch load, not an upgrade. Perhaps something to consider.

---

### Post by Kivech on 2011-05-13
> **patmagee1024 said:**
> I found a couple of other items in dmesg.

[   19.992717] pwc: Philips webcam module version 10.0.13 loaded.
[   19.992719] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   19.992720] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   19.992722] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   19.992740] pwc: Philips SPC 900NC USB webcam detected.
[   20.015165] pwc: Registered as /dev/video0.
[   20.018157] input: PWC snapshot button as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/input/input3
[   20.018212] usbcore: registered new interface driver Philips webcam

I had this device working under 9.10 before I reloaded to 10.04. Also, I did a scratch load, not an upgrade. Perhaps something to consider.

Did your webcam work out of the box, or did you have to install packages manually and configure them?

I'm asking since obviously our versions (600 & 700) don't work out of the box (anymore). Can't remember which Ubuntu version it was, but a couple of years ago mine did work just like that.

Did you install any particular drivers to get it to work? If so, please let us know which.

---

### Post by patmagee1024 on 2011-05-13
I recall having to piddle around with 3rd party drivers in 8.04. 9.10 and 10.04 seem to support this one out of the box. 

I located a place with a driver that is worth a try.

[http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)

Another is 

[http://www.all-driver.com/webcam-driver/philips-spc900nc-webcam-driver-xpvistalinux-download.html](http://www.all-driver.com/webcam-driver/philips-spc900nc-webcam-driver-xpvistalinux-download.html)

Hopefully these will help you find the right config.

---

### Post by slakov on 2011-05-20
> **patmagee1024 said:**
> I recall having to piddle around with 3rd party drivers in 8.04. 9.10 and 10.04 seem to support this one out of the box. 

I located a place with a driver that is worth a try.

[http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)

Another is 

[http://www.all-driver.com/webcam-driver/philips-spc900nc-webcam-driver-xpvistalinux-download.html](http://www.all-driver.com/webcam-driver/philips-spc900nc-webcam-driver-xpvistalinux-download.html)

Hopefully these will help you find the right config.

thanks! the pwc is outdated now, and the second one is windows driver? I am really giving up. The camera works on debian 6 with v4l2 but not in ubuntu. The guys messed up smth.

---

### Post by no2498 on 2011-05-20
the last one works with linux too

XP/Vista/Linux

---

### Post by Kivech on 2011-05-20
> **slakov said:**
> thanks! the pwc is outdated now, and the second one is windows driver? I am really giving up. The camera works on debian 6 with v4l2 but not in ubuntu. The guys messed up smth.

To be honest, I gave up also. Went to the local electronics store the other day and got me a new webcam for €15, plugged it in, and it works just like that.
Not too much of a big deal, but still a shame that I couldn't use a perfectly fine webcam.

Oh well, at least I have a working webcam now...

---

