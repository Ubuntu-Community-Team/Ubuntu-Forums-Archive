---
title: "Empia DC60+ blackscreen, EasyCAP"
date: 2013-09-01
forum: Multimedia Software
---

### Post by metra on 2013-09-01
Ubuntu 12.04 trying to get EasyCAP DC60+ to work. 

It is recognized and in VLC I get sound but no display.

Really, if we can get video but no sound that'd be great! I want to use it in Skype as a webcam.

From a thread I tried to [change the module]("http://ubuntuforums.org/showthread.php?t=1870921&highlight=rmmod+em28xx") 

```
sudo rmmod em28xx
sudo modprobe em28xx card=2
```

That was a bad idea my other cam also stopped working.

That was in 10.04 and being unable to download or reinstall from the cd I finally moved to 12.04

After poking around I got it working in skype and that got it to work in xawtv as well. Start up next day...not working at all. Below is what I have tried.

It is a fresh install. The empia did not work right of the box. The following is after an apt-get upgrade.

```
lsusb
```
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:0779 Microsoft Corp. 
Bus 002 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 004: ID eb1a:2861 eMPIA Technology, Inc. 
```
```
dmesg|grep em28
```
```
[ 5153.333991] em28xx: New device @ 480 Mbps (eb1a:2861, interface 0, class 0)
[ 5153.334172] em28xx #0: chip ID is em2860
[ 5153.424528] em28xx #0: board has no eeprom
[ 5153.499022] em28xx #0: found i2c device @ 0x4a [saa7113h]
[ 5153.526148] em28xx #0: Your board has no unique USB ID.
[ 5153.526154] em28xx #0: A hint were successfully done, based on i2c devicelist hash.
[ 5153.526158] em28xx #0: This method is not 100% failproof.
[ 5153.526160] em28xx #0: If the board were missdetected, please email this log to:
[ 5153.526163] em28xx #0: 	V4L Mailing List  <linux-media@vger.kernel.org>
[ 5153.526166] em28xx #0: Board detected as EM2860/SAA711X Reference Design
[ 5153.604030] em28xx #0: Identified as EM2860/SAA711X Reference Design (card=19)
[ 5153.604036] em28xx #0: Registering snapshot button...
[ 5153.604180] input: em28xx snapshot button as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/input/input8
[ 5153.980545] saa7115 14-0025: saa7113 found (1f7113d0e100000) @ 0x4a (em28xx #0)
[ 5154.748199] em28xx #0: Config register raw data: 0x10
[ 5154.772074] em28xx #0: AC97 vendor ID = 0x83847652
[ 5154.784068] em28xx #0: AC97 features = 0x6a90
[ 5154.784071] em28xx #0: Sigmatel audio processor detected(stac 9752)
[ 5155.244085] em28xx #0: v4l2 driver version 0.1.3
[ 5156.268551] em28xx #0: V4L2 video device registered as video1
[ 5156.268557] em28xx #0: V4L2 VBI device registered as vbi0
[ 5156.268617] usbcore: registered new interface driver em28xx
[ 5156.268621] em28xx driver loaded
```

So far so good. 

In VLC I get sound but black screen. To forums!

Try to install Mythbuntu and that goes horribly. Had problems with it connecting to the database it created. I un-installed as it was just another problem.


```
mplayer tv://-tv driver=v4l2:norm=PAL:outfmt=uyvy:device=/dev/video1:input=0:fps=25-vo xv
```
```
mplayer tv://-tv driver=v4l2:norm=NTSC_M_JP:output=0:device=/dev/video1 -vo xv -fs
```

Output: video from dev/video0 (The Microsoft webcam)

VLC from gui gave a black box with blurry white word overlay "v4l2///dev/video1

Installed Medibuntu from [the this is ALL the media thread]("http://ubuntuforums.org/showthread.php?t=766683")
rebooted. Same result as before. 

Installed xawtv as there were several threads recommending it for related issues.

```
xawtv -hwscan 
```
```
This is xawtv-3.102, running on Linux/i686 (3.2.0-23-generic)
looking for available devices
port 76-91
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

port 92-92
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : libv4l
    name : Microsoft® LifeCam HD-3000
    flags:  capture  

/dev/video1: OK                         [ -device /dev/video1 ]
    type : libv4l
    name : EM2860/SAA711X Reference Design
    flags:  capture 
```

```
xawtv -remote -noxv -c /dev/video1 -noalsa
```
```
This is xawtv-3.102, running on Linux/i686 (3.2.0-23-generic)
xinerama 0: 1280x1024+0+0
```

I disabled sound since alsa kept displaying this error:
```
alsa: stream started from hw:2,0 to default (8000 Hz, buffer delay = 30.00 ms)
ALSA lib pcm.c:7339:(snd_pcm_recover) overrun occurred
```

With alsa off it showed a black box.

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```

[B]Got it working on skype! hurray!

Next day...not working O.o Back to a black screen, no VLC sound.[/B]

Nada.

Ideas?

---

### Post by metra on 2013-09-01
Maybe someone can help figure out how to read a driver page.

from dmesg my card is identified as:
```
[ 5153.526166] em28xx #0: Board detected as EM2860/SAA711X Reference Design
[ 5153.604030] em28xx #0: Identified as EM2860/SAA711X Reference Design (card=19)
```

However the box says it's 2861. 

Several of the threads have futzing around with the driver as the solution

```
sudo rmmod em28xx
sudo modprobe em28xx card=2
```
Though there are some suggesting 19 or 12-25 as the value for card.

I found a copy of the driver online [http://linuxtv.org/hg/v4l-dvb/file/tip/linux/drivers/media/video/em28xx/em28xx-cards.c](http://linuxtv.org/hg/v4l-dvb/file/tip/linux/drivers/media/video/em28xx/em28xx-cards.c)

(If someone could tell me how to either read a .ko file or how to find this file on my system that'd be ideal)

However assuming that the above file is essentially the same as mine there are card values that I'd like to try. Namely, one called   [EM2860_BOARD_EASYCAP] and all the EM2861 board cases.

The problem is that while dmesg has the card=19, EM2860/SAA711X Reference Design is not #19 in the list of board definitions :confused: 

I don't understand how the switch statement (or struct?) is numbering the cards. Help!

I'd rather not plug in card numbers as that somehow disabled my other webcam in 10.04.

If not here, where would be a better place to ask for help for reading the device driver?

Or, is there another way to detect the board type? Is it that dmesg detected incorrectly or that the box it came in is labled wrong

---

