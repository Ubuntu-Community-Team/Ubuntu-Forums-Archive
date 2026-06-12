---
title: "Webcam problem Logitech QuickCam Pro for Notebooks"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by tudsy on 2006-08-20
Hey y'all.   I've managed to get everything working except my webcam.
I've tried webcam, I think I even managed to install the UVC driver which in theory supports my webcam (Logitech QuickCam Pro for Notebooks, 046d:08c3),
but when I try to launch any program that needs to access it, I get a "cannot connect to video device dev/video0".  There is a video0 listed under dev, but nothing can open it, apparrently. 

Any wisdom?

---

### Post by foolsh on 2006-08-20
do you know which driver the webcam uses? like ov511 or spca5xx.

type lsmod in a terminal will show you what modules are loaded
modules are drivers

you can also use pipe "not tubes" and grep to search output that is otherwise to long to drudge through

lsmod | grep ov51*
lsmod | grep spca*

---

### Post by Fingolfin on 2006-08-20
I have a similar problem. Purchased Logitech QuickCam 5000 Pro after finding it on the list of supported webcams at 
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

I then followed step-by-step guide for Dapper from this thread:
[http://www.ubuntuforums.org/showthread.php?t=75284&highlight=logitech+usb+cam](http://www.ubuntuforums.org/showthread.php?t=75284&highlight=logitech+usb+cam)
but the device has not been installed.

When I run Ekiga for example, the sound works fine, testing the camera's microfone went ok, but in the video devices section it simply says "no video device found" with Video Plugin V4L.

The following commands give no return information at all:

$sudo lsmod | grep spca*
$sudo modprobe spca5xx

Any ideas on how to activate the cam?

---

### Post by tseliot on 2006-08-20
> **Fingolfin said:**
> I have a similar problem. Purchased Logitech QuickCam 5000 Pro after finding it on the list of supported webcams at 
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

I then followed step-by-step guide for Dapper from this thread:
[http://www.ubuntuforums.org/showthread.php?t=75284&highlight=logitech+usb+cam](http://www.ubuntuforums.org/showthread.php?t=75284&highlight=logitech+usb+cam)
but the device has not been installed.

When I run Ekiga for example, the sound works fine, testing the camera's microfone went ok, but in the video devices section it simply says "no video device found" with Video Plugin V4L.

The following commands give no return information at all:

$sudo lsmod | grep spca*
$sudo modprobe spca5xx

Any ideas on how to activate the cam?
Usually there's no need to modprobe the module on Dapper.

My quickcam (not the same as the thread starter's) works in this way:
Plug in your webcam (I guess you can't since it is embedded in the notebook
Then open Ekiga. Get to Edit/preferences/Video Device. And select the input device.
Exit from the Preferences menu.
Click on the icon of a webcam (on Ekiga's interface)
And you should see the images from your webcam.


NOTE: Mine doesn't work in AMSN.

---

### Post by teyster2 on 2006-08-20
I wanted to use my Ezonics, EZ CamII with Kopete (Kubuntu) so I installed the SPCA5 program with adept and it worked except the image is upside down. Not a big problem as I can velcro it under my desktop shelf and get an upright image, but I would like to, if anyone knows how, right the image. :-k

---

### Post by Fingolfin on 2006-08-20
> **tseliot said:**
> 
Then open Ekiga. Get to Edit/preferences/Video Device. And select the input device.

That's exactly where the problem is. I cannot select the Input Device ("No device found"). Nothing happens also after clicking the "Detect devices" button.

$lsusb | grep Logitech  gives the following output:

Bus 001 Device 004: ID 046d:08c5 Logitech, Inc.

(If that's of any relevance here, Logitech QuickCam Pro 5000 is not a notebook model, but standard usb webcam.)

---

### Post by foolsh on 2006-08-20
ok did some research and it looks like there is a new branch of the spca5xx driver look [here]("http://mxhaard.free.fr/download.html") well I dont own a spca5xx camera but I do own two ov51x cams that needed some extra help to get working. Here is my [how-to]("http://foolsh.home.insightbb.com/")
I am willing to help but I can't be right there beside you so here is what I would do if I was
 
```
sudo apt-get install build-essential linux-headers-`uname -r`

wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz

tar -xvf spca5xx-20060501.tar.gz

cd spca5xx-20060501

make 

sudo rmmod spca5xx

sudo make install

sudo update-modules

sudo modprobe spca5xx
```

then I would try a simple app like xawtv

```
sudo apt-get install xawtv

xawtv -c /dev/video0
``` 
video0 if it is the only video input device you have

---

### Post by Fingolfin on 2006-08-20
Thanks guys for quick replies.
I followed this approach and got the following error after completing the sequence of commands:

$ sudo modprobe spca*
FATAL: Module spca5xx.ko not found.

It appears that the driver is not loaded into the kernel?!


This was the output from the make install command:

$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
/sbin/depmod -ae


When attempted to 'remove' the previously installed version of the spca driver (as I thought it would have been installed), another message appears suggesting that was not the case:

$ sudo rmmod spca5xx
ERROR: Module spca5xx does not exist in /proc/modules

---

### Post by foolsh on 2006-08-20
try
```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
```

---

### Post by foolsh on 2006-08-20
then try your video app

---

### Post by Fingolfin on 2006-08-21
I took your advice and recorded actions to trace my steps back. Spooky things started to appear after I have finished with:

$ sudo update-modules
$ sudo modprobe spca5xx

the command
$ lsmod   (and $ lsmod > lsmod.txt)

Module                  Size  Used by
spca5xx               664592  0
videodev                9856  1 spca5xx

showed in the very first two lines that the module has finally been loaded.

Unfortunately, when I went to Ekiga in Edit/Preferences/Video Devices it was still the same: Video plugin V4L and No device found.

After rebooting, lsmod showed no sign of spca5xx so I am at the beginning again.

---

### Post by foolsh on 2006-08-21
I would try a simple program like xawtv to rule out if the camara was working or not. It maybe a problem with  Ekiga

---

### Post by Fe01 on 2006-08-30
Hiya

same here

is there some wisdom left for me too :p 

original post: [http://www.ubuntuforums.org/showpost.php?p=1439857&postcount=265](http://www.ubuntuforums.org/showpost.php?p=1439857&postcount=265)

Can you advise me plz:

-installation went fine

-lsmod:
spca5xx               664592  0
videodev                9856  1 spca5xx
usbcore               130692  9 spca5xx,usb_storage,usbhid,snd_usb_audio,snd_usb_lib,hci_usb,ehci_hcd,uhci_hcd

-lsusb
Bus 004 Device 007: ID 046d:08c3 Logitech, Inc.
Bus 004 Device 004: ID 041e:3020 Creative Technology, Ltd SoundBlaster Audigy 2 NX
Bus 004 Device 006: ID 0ea0:2118 Ours Technology, Inc.
Bus 004 Device 005: ID 046d:c01d Logitech, Inc.
Bus 004 Device 002: ID 050d:0237 Belkin Components
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

-/dev/ appeared after connection
audio2
dsp2
mixer2
no video

-dmesg
[17179720.416000] Linux video capture interface: v1.00
[17179720.548000] usbcore: registered new driver spca5xx
[17179720.548000] /drivers/usb/spca5xx.c: spca5xx driver 00.60.00 registered
[17179743.700000] usb 4-2: new high speed USB device using ehci_hcd and address 7
[17179745.008000] 7:3:1: cannot set freq 0 to ep 0x86
[17179746.008000] 7:3:2: cannot set freq 0 to ep 0x86
[17179746.976000] 7:3:3: cannot set freq 16000 to ep 0x86

I'm running Kubuntu Dapper 2.6.15-26-386.
Webcam is 046d:08c3 Logitech QuickCam for Notebooks Pro.

Acoording to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) support is written "TEST" and the driver Linux-UVC:
Logitech	2	0x046d	0x08c3	QC pro for Notebooks	Sunplus	spca525a	 	Test	mjpeg	linux-UVC	********

Does that just mean that I have to install in addition this BerliOS driver?

Has anyone done it before here?

Thanks a lot in advance!


**FOR DAPPER**
If you are on Dapper do the following instead of the above:
```
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential
wget http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz
tar xvfz spca5xx-20060501.tar.gz
cd spca5xx-20060501
make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx
```[/QUOTE]

---

### Post by leenke on 2006-09-29
> **tudsy said:**
> Hey y'all.   I've managed to get everything working except my webcam.
I've tried webcam, I think I even managed to install the UVC driver which in theory supports my webcam (Logitech QuickCam Pro for Notebooks, 046d:08c3),
but when I try to launch any program that needs to access it, I get a "cannot connect to video device dev/video0".  There is a video0 listed under dev, but nothing can open it, apparrently. 

Any wisdom?

I have the same one. but i don't know how i have to install linux-uvc. when i try to install it, i always get a error:
Building USB Video Class driver...
/bin/sh: line 0: cd: /lib/modules/2.6.15-27-686/build: Onbekend bestand of map
make: *** [uvcvideo] Fout 1

i'm sorry my computer is in dutch, but it means that that file doesn't exict. i don't know what i have to do to make my webcam work on linux.

can someone help me?

---

### Post by fbolduc on 2007-01-05
I have done some extensive search and testing on this one. I found some wisdom, but I was not able to make my Logitech QuickCam Pro for Notebook work properly. This is the 046d:08c3 model as shown by the following command:

```


$ lsusb
Bus 003 Device 006: ID 046d:08c3 Logitech, Inc.
```

_I tested the following drivers:_

SPCA5xx [COLOR="Red"]did not work[/COLOR]
GSPCA [COLOR="Red"]did not work[/COLOR]
PWC [COLOR="Red"]did not work[/COLOR]
UVC ([http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)) [COLOR="Lime"]almost worked[/COLOR]

The UVC driver almost worked. I was able to grab a jpeg picture and an avi video using a special application ([http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz)) that, unlike camorama, xawtv, ekiga and others, understands the uncommon MJPEG stream that the Logitech QuickCam Pro for Notebook outputs. MJPEG has been criticized by many and does not have a well defined standard. I guess Logitech is not keen about using popular and efficient codecs.

However, the application only worked once. The /dev/video device is created by the driver when I connect the WebCam, but, for some reason, cannot be initialized twice so I could not get it to work again unless I rebooted. Is it the application? Is it the driver? I can't tell.

I'm giving up for now.

Anybody willing to take it from here would be wise to read [http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC) for starter.

I hope this will help other people to find a solution.

Best of luck,
Francis

---

### Post by ramjet_1953 on 2007-01-08
The plot thickens on this.
When I was using Dapper, my Logitech QuichCam for Notebooks Pro worked flawlessly.
If you have a look on a Dapper install the following directory exists:

/lib/modules/2.6.15-27-686/kernel/drivers/usb/media/
(The kernel number obviously is dependant upon your particular install.)

There are drivers for several cameras in the /media directory.

There are sub-directories under this for:

ov511, poxtpro, pwc, quickcam, spca5xx

The /media directory doesn't even exist under an Edgy install, so the kernel is not enabled for webcams. For some unknown reason, this has been left out.

I know that several cameras use the Philips driver, Logitech for example and that there is some sort of battle raging with the writer of the spca5xx drivers, so I imagine that he has pulled permission to have these drivers included in the kernel. This is only speculation.

Anyhow, the end result is that we have literally been left in the dark.

Regards,
Roger 8)

---

### Post by blacksun on 2007-09-06
Hi I just bought a logitech quickcam pro for notebooks and it's not automatically detected/working with ubuntu. My older logitech quickcam works but is very annoying to use since it's has no clip for my notebook. 

Anyway , I noticed the following directory in feisty's latest kernel:
```

blacksun@blacksun-laptop:/usr/src$ tree /lib/modules/2.6.20-16-generic/kernel/ubuntu/media/
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/
|-- gspcav1
|   `-- gspca.ko
|-- ivtv
|   |-- ivtv-fb.ko
|   |-- ivtv.ko
|   `-- saa717x.ko
|-- ov511
|   `-- ov511.ko
|-- quickcam
|   `-- quickcam.ko
`-- usbvideo
    `-- uvcvideo.ko

```
Modprobing those modules doesn't help. 

After that i installed spca5xx-source. According to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
it should work with my webcam.
apt-get install spca5xx-source
blacksun@blacksun-laptop:/usr/src$ dpkg -l | grep  spca
ii  spca5xx-source                             20060501-2ubuntu2                      source for the spca5xx driver

I do not want to recompile my whole kernel. The documentation says i should untar the package and issue these commands:
```

Please install the module-assistant package and issue the following commands
in a shell:-
  $ m-a prepare
  $ m-a a-i spca5xx

m-a is short for module-assistant, and a-i is short for auto-install. Please
see the module-assistant documentation for futher details about this process.

```

Has somebody done this before?

---

### Post by iammeagain on 2007-12-09
> **blacksun said:**
> Hi I just bought a logitech quickcam pro for notebooks and it's not automatically detected/working with ubuntu. My older logitech quickcam works but is very annoying to use since it's has no clip for my notebook. 

Anyway , I noticed the following directory in feisty's latest kernel:
```

blacksun@blacksun-laptop:/usr/src$ tree /lib/modules/2.6.20-16-generic/kernel/ubuntu/media/
/lib/modules/2.6.20-16-generic/kernel/ubuntu/media/
|-- gspcav1
|   `-- gspca.ko
|-- ivtv
|   |-- ivtv-fb.ko
|   |-- ivtv.ko
|   `-- saa717x.ko
|-- ov511
|   `-- ov511.ko
|-- quickcam
|   `-- quickcam.ko
`-- usbvideo
    `-- uvcvideo.ko

```
Modprobing those modules doesn't help. 

After that i installed spca5xx-source. According to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
it should work with my webcam.
apt-get install spca5xx-source
blacksun@blacksun-laptop:/usr/src$ dpkg -l | grep  spca
ii  spca5xx-source                             20060501-2ubuntu2                      source for the spca5xx driver

I do not want to recompile my whole kernel. The documentation says i should untar the package and issue these commands:
```

Please install the module-assistant package and issue the following commands
in a shell:-
  $ m-a prepare
  $ m-a a-i spca5xx

m-a is short for module-assistant, and a-i is short for auto-install. Please
see the module-assistant documentation for futher details about this process.

```

Has somebody done this before?


Did this work? I also have a Quickcam Pro for Notebooks, and want to know how to make it work. It is not detected as I can see. I tried using ekiga, I don't really know what programs webcam support actually works and which don't.  
I want to get it working to talk to my girlfriend through msn messenger.

---

### Post by BrewBelly on 2007-12-15
Bump.

Has anyone gotten a QuickCam for Notebooks Pro to work?

---

### Post by ImNeat on 2007-12-16
> **BrewBelly said:**
> Has anyone gotten a QuickCam for Notebooks Pro to work?

I was able to get mine working with Ekiga  out of the box without problem.  I installed camstream and used Video 4 Linux 2.  Works great so far.  Just trying to find a good app like iMovie that can view live stream.

---

### Post by iammeagain on 2007-12-20
> **ImNeat said:**
> I was able to get mine working with Ekiga  out of the box without problem.  I installed camstream and used Video 4 Linux 2.  Works great so far.  Just trying to find a good app like iMovie that can view live stream.

I got it working with amsn somehow, it seemed almost just to decide to work. But I have no audio. I don't know how to get use Ekiga with someone on Windows Messenger/Msn messenger. Its UI is different and I don't understand a lot of what it asks for. 
If anyone has any good links on how to use it with msn please post. I looked but didn't find much that  I could make sense of. Thank you in advance.

---

### Post by BrewBelly on 2008-01-06
Thanks ImNeat,

I can get an image (a dark, crappy one) in Ekiga, but nothing else.  I use  a lot of FLASH-based video conference (like Stickam), and hardly ever use one-on-one like ekiga.

oh well, I still have reasons to keep XP on a partition for now.

---

### Post by spegru on 2008-01-08
I just got one of these, to use with Skype
Didnt work at first - jaggy lines and green stripes, but then for no obvious reason it started to work.
Frame rate seems slow, which may ne because of its high resolution

Nothing else seems to be able use it so far though.

spegru

---

### Post by batinov on 2008-04-01
Logitech Pro for Notebooks works fine with Ekiga, excellent video and audio quality.

I got it running with the UVC driver and V4L2.

To check if UVC is on, type

```
lsmod | grep uvc
```

and you should get

```
uvcvideo               52104  0 
compat_ioctl32          1408  1 uvcvideo
videodev               26304  1 uvcvideo
v4l1_compat            12580  2 uvcvideo,videodev
v4l2_common            16608  2 uvcvideo,videodev
usbcore               132940  7 uvcvideo,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd

```

You must have Video4Linux2 installed.

If you have uvc loaded,  check to see if you have the camera recognized:

Type:

```
lsusb | grep Logitech
```

and you should see

```
Bus 003 Device 002: ID 046d:0991 Logitech, Inc. 
```

As root, type:
 
```
ls /dev/vid*
```

and you should see:

```
/dev/video0
```

Then, to test the device, type as root:

```

aptitude install xawtv
xawtv -c /dev/video0

```

xawtv should display a video stream.  

If the camera is connected and giving you footage as root, but Ekiga doesn't see it in the configuration wizard, you need to make sure you can access /dev/video0 as a non-root user.  Do the following:

1. Select V4L2 as your video plugin in Ekiga
2. as root, type

```
chmod 777 /dev/video0
```

Make sure to click the camera icon in Ekiga, as under Linux it doesn't start displaying footage automatically.

That took awhile to figure out. Best of luck!

---

