---
title: "webcam woes - works once and stops"
date: 2010-02-28
forum: Multimedia Software
---

### Post by pickarooney on 2010-02-28
I got a new webcam, plugged it in and tested in Skype. Nothing doing, the Test button simply doesn't respond.

So I installed cheese and ran it. Webcam was fine. Then I changed the resolution down and it was still OK. Finally I changed it back and now the webcam doesn't work any more. Instead of seeing a feed, I see a TV-style test card and white noise in the bottom right corner. I tried uninstalling and reinstalling, as well as restarting X, but it's as if my webcam broke after 30 seconds use (I'm not THAT ugly, I swear :D)

I've tried the PRELOAD and EXPORT commands that sometimes help to run skype, but there's no improvement there.

---

### Post by collinge on 2010-02-28
try looking in ALT F2 g-streamer properties

also try installing wxcam

I have had lots of webcam issues with linux... its kind of a touchy subject.

You can also look in the package manager for your webcam driver... Good luck

---

### Post by pickarooney on 2010-02-28
I can't install wxcam; last time I tried it needed dependencies I couldn't use.
I wonder is the settings file for cheese stored anywhere so I could delete it and at least get that to capture again?

gstreamer properties gives me that same testcard thing unfortunatey :(

---

### Post by prshah on 2010-02-28
> **pickarooney said:**
> a TV-style test card and white noise in the bottom right corner. 

Do you also have a tv tuner card and/or other video source? There is no webcam I know of that will give you this kind of output. Maybe it may be as simple as not selecting the correct video device; check your available video devices from the terminal (Applications-Accessories-Terminal) ```
ls /dev/video*
```if you get more than 2 video devices (video0, video1...) check each with the command```
cvlc v4l2:///dev/video0
``` (note that it's 3 forward slashes after the colon ":").

If these tips don't work out, unplug your webcam, wait a couple of seconds, then plug in your webcam, wait about 10 seconds, then open the terminal and post back the output of these  commands```
tail -20 /var/log/messages
lsusb
```

---

### Post by pickarooney on 2010-02-28
> **prshah said:**
> Do you also have a tv tuner card and/or other video source? There is no webcam I know of that will give you this kind of output. 


Yes, the two tend to be assigned video0 and video1 by the system on alternate boots. When I select the tuner in cheese I get a tv signal; when I select Webcam I get that testcard thing.

```
cvlc v4l2:///dev/video0
``` 

With video0 I get nothing, teh last lines of output are:
```

[00000001] main libvlc debug: translation test: code is "en_GB"
[00000384] main interface error: no interface module matched "screensaver,none"
[00000384] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000387] dummy interface: using the dummy interface module...

```

With video1 I get the sound of the TV and a bizarre ASCII video display.

```
tail -20 /var/log/messages
lsusb
```

gives:

```

Feb 28 17:14:32 marklar cairo-dock: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:14:32 marklar cairo-dock: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:14:39 marklar Thunar: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:15:56 marklar Thunar: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:15:56 marklar cairo-dock: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:15:56 marklar Thunar: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:15:56 marklar cairo-dock: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:15:56 marklar xfdesktop: Trash directory /media/bigbastard/.Trash-1000 exists, but didn't pass the security checks, can't use it
Feb 28 17:15:56 marklar last message repeated 2 times
Feb 28 17:15:58 marklar kernel: [ 9711.016250] usb 3-4: USB disconnect, address 3
Feb 28 17:34:32 marklar -- MARK --
Feb 28 17:54:32 marklar -- MARK --
Feb 28 18:14:32 marklar -- MARK --
Feb 28 18:34:32 marklar -- MARK --
Feb 28 18:42:16 marklar kernel: [14889.013966] usb 1-3: USB disconnect, address 6
Feb 28 18:42:35 marklar kernel: [14907.184048] usb 1-3: new high speed USB device using ehci_hcd and address 8
Feb 28 18:42:35 marklar kernel: [14907.408881] usb 1-3: configuration #1 chosen from 1 choice
Feb 28 18:42:35 marklar kernel: [14907.410941] uvcvideo: Found UVC 1.00 device Webcam 3300 (04f2:a134)
Feb 28 18:42:35 marklar kernel: [14907.416129] input: Webcam 3300 as /devices/pci0000:00/0000:00:13.2/usb1/1-3/1-3:1.0/input/input10
Feb 28 18:42:35 marklar kernel: [14907.483203] 8:3:1: cannot get freq at ep 0x84

```


edit: most importantly, the webcam works in cheese after plugging it out and in again - I has forgotten to check!

---

### Post by pickarooney on 2010-02-28
Well, cheese has stopped working again, tv testcard instead, and plugging the cam out and in has not fixed it. It may be when I try to run skype that it gets messed up...

---

### Post by pickarooney on 2010-03-01
Is there some way to temporarily disable the TV tuner without removing it physically, so I can at lest test the webcam as the sole /dev/video device on the system and see if the testcard thing is related to that?

---

### Post by pickarooney on 2010-03-01
I tried luvcview also, but got this...

```

luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: MJPG
Unable to set format: Device or resource busy
 Init v4L2 failed !! exit fatal

```

---

### Post by pickarooney on 2010-03-02
Same problem in Mint with a live CD... this is nuts

---

### Post by typos1 on 2010-03-02
I ve got smilar probs-amsn (only app I use webcam for) recognises both my tv cards (unused currently), but not my Trust webcam, but if I type lsusb in a terminal, it recognises it.

---

### Post by pickarooney on 2010-03-02
I tried plugging the webcam into my laptop, also running jaunty, and it worked straight away in skype. Then plugged it back into the desktop and it now works, for the moment, in cheese. Still no dice in skype, but I think cairo-dock is messing with it.

Also, if I run LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so then not only does skype not work but cheese stops working again after.

---

### Post by no2498 on 2010-03-02
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to    x window system (no xv)
an do not open cheese

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/) read what he says to install

also you can get in a deb file

---

### Post by pickarooney on 2010-03-03
OK, I think it works OK as long as I don't run skype and don't use the LD_PRELOAD command that used to work in Skype a while ago. 

Now I just need to find a way to make skype work

---

### Post by pickarooney on 2010-03-03
I got skype to work with export XLIB_SKIP_ARGB_VISUALS=1 && skype

ONCE

then there was no pciture any more, just that stupid test card crap.

So frustrating.

---

### Post by pickarooney on 2010-03-03
> **no2498 said:**
> open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to    x window system (no xv)
an do not open cheese

also you can get in a deb file

Same thing -stupid testcard rubbish comes up.

screenshot attached, for those interested.

---

