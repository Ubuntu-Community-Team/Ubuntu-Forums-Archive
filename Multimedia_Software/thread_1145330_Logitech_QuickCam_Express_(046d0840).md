---
title: "Logitech QuickCam Express (046d:0840)"
date: 2009-05-01
forum: Multimedia Software
---

### Post by rapha on 2009-05-01
Hi all,

I'm trying to get my (admittedly ancient) Logitech QuickCam Express to work again under Jaunty. Up to Hoary it had always worked out-of-the-box like a charm, but then stopped working magically.

So far I found out that I need a think called qc-usb ([http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)), and have compiled it from Ubuntu's qc-usb-source package. After loading the driver with "modprobe quickcam" I can use the webcam in Camorama and *only* there.

As for other software: Ekiga and Cheese both show to be selected in their settings but say it doesn't work when you try it out. XawTV just shows a black screen. Skype plain crashes, showing the following console output:

```
rapha@flow:~$ skype
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
Skype V4L: Device does not support video capture
Starting the process...
Skype Xv: Xv ports available: 64
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 355
Skype Xv: No suitable overlay format found
Aborted
```

Can anybody help out? :(

Best regards,
Raphael

---

### Post by newagelink on 2009-06-04
I also receive the error messages using a fresh Ubuntu 9.04 installation: ```
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
``` Wish I could help. I guess I should read about ALSA.

---

### Post by rapha on 2009-06-04
I'm not even sure your problem is related with a QuickCam at all ;-) - Maybe repost under a different title, should get you better chances of being helped...

Regards, Raphael

---

### Post by GeoMX on 2009-07-20
> **rapha said:**
> 
So far I found out that I need a think called qc-usb ([http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)), and have compiled it from Ubuntu's qc-usb-source package.
Hi rapha, could you give some more details about how you got it compiled? I downloaded the qc-usb-source package from the repositories but have not been able to compile it.

When typing "make", I get this:
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/josejorge/modules/qc-usb modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-13-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-13-generic'

But when typing sudo make install, I get lots of errors from qc-driver.c file.

Thanks in advance for your help.

---

### Post by rapha on 2009-07-20
Hi GeoMX,

I compiled it following the hints from [https://bugs.launchpad.net/ubuntu/+source/qc-usb/+bug/213114](https://bugs.launchpad.net/ubuntu/+source/qc-usb/+bug/213114)

Cheers,
Raphael

---

### Post by GeoMX on 2009-07-22
Thank you so much for your help, as stated on that discussion, the latest Ubuntu source package is supposed to have that bug corrected, I managed to install qc-usb using module-assistant, but now my whole system crashes when trying to access the webcam :(. I'll try to find the problem.

Anyway, thanks :).

---

### Post by ran_talbott on 2009-10-29
Does anyone have this camera (or the Lego variant that also uses the quickcam driver) working reliably on *any* version of Linux (preferably Ubuntu,  but I'll take anything at this point)?

After reading this post,  I tried setting up a Gutsy system,  but all I achieved was replacing the system crashes I'm getting with Hardy (see [this thread]("http://ubuntuforums.org/showthread.php?t=1301852")) with kernel panics.

Thanks,

Ran

---

### Post by serendipitousus on 2010-02-16
I'm having the same issue you were having. 

```

me@Machine:~$ lsusb
.
.
Bus 004 Device 003: ID 046d:0840 Logitech, Inc. QuickCam Express
.

```

```

me@Machine:~$ dmesg | tail -7 
[ 2534.748062] usb 4-3: new full speed USB device using ohci_hcd and address 3
[ 2534.995861] usb 4-3: configuration #1 chosen from 1 choice
[ 2534.997527] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[ 2534.997537] quickcam: Kernel:2.6.28-18-generic bus:4 class:FF subclass:FF vendor:046D product:0840
[ 2535.048765] quickcam: Sensor HDCS-1000/1100 detected
[ 2535.053559] quickcam: Registered device: /dev/video0

```

The device is listed under /dev/video0, when I try to take a picture via streamer, I get the following 

```
me@Machine:~$ sudo streamer -c /dev/video0 -b 16 -o TestCam.jpeg
files / video: JPEG (JFIF) / audio: none
libv4l2: error getting capabilities: Unknown error 515
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Unknown error 515
v4l: capture not supported

```

Which leads me to believe the issue with the 046d:0840 model is that its not recognized by HAL as a v4l capable device.

Here's the relevant output from lshal

```

udi = '/org/freedesktop/Hal/devices/usb_device_46d_840_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_1'  (string)  
  info.product = 'QuickCam Express'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_840_noserial'  (string)
  info.vendor = 'Logitech, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/004/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb4/4-3'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)  
  usb_device.device_class = 255  (0xff)  (int)
  usb_device.device_protocol = 255  (0xff)  (int)
  usb_device.device_revision_bcd = 256  (0x100)  (int)
  usb_device.device_subclass = 255  (0xff)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb4/4-3'  (string)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)  
  usb_device.product = 'QuickCam Express'  (string)
  usb_device.product_id = 2112  (0x840)  (int)  
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Logitech, Inc.'  (string)
  usb_device.vendor_id = 1133  (0x46d)  (int)
  usb_device.version = 1.0 (1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_840_noserial_if0'
  info.linux.driver = 'quickcam'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_840_noserial'  (string)
  info.product = 'USB Vendor Specific Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_840_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb4/4-3/4-3:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.device_class = 255  (0xff)  (int)
  usb.device_protocol = 255  (0xff)  (int)
  usb.device_revision_bcd = 256  (0x100)  (int)
  usb.device_subclass = 255  (0xff)  (int)
  usb.interface.class = 255  (0xff)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 255  (0xff)  (int)
  usb.interface.subclass = 255  (0xff)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb4/4-3/4-3:1.0'  (string)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Vendor Specific Interface'  (string)
  usb.product_id = 2112  (0x840)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 1.0 (1) (double)

```

If I'm on the right track, there's a launchpad bug related to this problem. 

[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/196811](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/196811)

Hope some of this information is useful, and if someone could walk us through working this issue out, that'd be most appreciated.

---

### Post by koanhead on 2010-02-16
I'll throw in my two cents here, even though my camera is slightly different (Quickcam 4000- 046d:08b2) and so are the problems I'm experiencing with it. 
I'm using the pwc module, and the webcam worked for a week or so, providing images in color but streaky and with low resolution. Camera works in Cheese and Camorama but not detected or usable by Flash. After the first week or so it continues to work but only in black-and-white.

---

### Post by serendipitousus on 2010-02-16
> **koanhead said:**
> I'll throw in my two cents here, even though my camera is slightly different (Quickcam 4000- 046d:08b2) and so are the problems I'm experiencing with it. 
I'm using the pwc module, and the webcam worked for a week or so, providing images in color but streaky and with low resolution. Camera works in Cheese and Camorama but not detected or usable by Flash. After the first week or so it continues to work but only in black-and-white.

Hmm...

I'm using the quickcam module, that came with the qc-usb package. I believe that's being set up and used correctly. 

```

me@Machine: ~$ lsmod
.
.
quickcam               80928  0 
videodev               41600  1 quickcam
v4l1_compat            21764  1 videodev
.

```

The above suggests to me its being recognized as v4l1, and not v4l2 compatible, although I'd like someone more experienced to let me know. Its listed [http://moinejf.free.fr/webcam.html]("http://moinejf.free.fr/webcam.html") as a v4l2 capable webcam (although using the gspca module?)

[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams") This page seems to suggest that I might need to try a different module if I want it to work at all, but that's an older post, so I'm not sure how much stock to put in it. 

Again, if anyone has ideas on how to get this working, or can clear up some of my misconceptions, it'd be greatly appreciated.

---

### Post by no2498 on 2010-02-17
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button

now all you need is a program to see an use it in

get cheese and wxcam

most all webcam's work out of the box now days

---

### Post by serendipitousus on 2010-02-18
> **no2498 said:**
> open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button

now all you need is a program to see an use it in

get cheese and wxcam

most all webcam's work out of the box now days

Iinteresting. This gets me a new swath of error messages, which I assume are related to my previous problem. 

When I run it from the command line, I get a few 'unavailable plugin' messages, and then ones I think to be an effect of the problem I'm having.

```

me@Machine:~$ sudo gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(198): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc3:
Device opened, but wrong type (0x0)]

```

The GUI opens, and when I move to video I have two options for device,  'default' or 'unknown'. I'm choosing unknown, because that the pipeline lists /dev/video0, which is where my webcam is loaded. When I select it and hit Test for v4l1, I get the following error message in terminal:

```

gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(198): gst_v4l_open (): /GstPipeline:pipeline3/GstV4lSrc:v4lsrc7:
Device opened, but wrong type (0x0)]

```

and the GUI displays a box stating: 

"Video for Linux (v4l): Could not get/set settings from/on resource."

When I select v4l2, I get this message in terminal:

```

libv4l2: error getting capabilities: Unknown error 515

```

When I hit Test for v4l2, I get a different error message in terminal: 

```

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver. [v4l2_calls.c(95): gst_v4l2_get_capabilities (): /GstPipeline:pipeline4/GstV4l2Src:v4l2src5:
system error: Unknown error 515]


```

and the following message in GUI:

"Video for Linux 2 (v4l2): Error getting capabilities for device '/dev/video0': It isn't a v4l2 driver. Check if it is a v4l1 driver."

Again, I'm rather lost as to what to do. I'm seeing this 515 error fairly often from the v4l2src. If someone could shed some light there, it'd be of great help.

---

### Post by serendipitousus on 2010-02-19
I got one other what might be useful error message from xawtv

```

me@Machine:~$ sudo xawtv -v
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-18-generic)
xinerama 0: 1280x1024+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
libv4l2: error getting capabilities: Unknown error 515
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Unknown error 515
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
station "-v" not found

```

I don't know if this is of use.

Also: I've made sure to test the hardware, and it functions perfectly in a Windows environment, so the issue is software side.

---

### Post by serendipitousus on 2010-02-22
I've also tried patching the module as described here. 

[http://jeffrasmussen.wordpress.com/2009/02/04/ubuntu-quickcam-express/]("http://jeffrasmussen.wordpress.com/2009/02/04/ubuntu-quickcam-express/") 

The link described a similar sounding error in 8.04. I successfully built the module after applying the patches, but this seemed to have no impact.

---

### Post by serendipitousus on 2010-02-24
Huh.. here's another bit of information.

When using it through flash, it works perfectly.

---

