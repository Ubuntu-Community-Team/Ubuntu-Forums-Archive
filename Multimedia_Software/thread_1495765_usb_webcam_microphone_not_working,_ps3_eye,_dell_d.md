---
title: "usb webcam microphone not working, ps3 eye, dell d630, ubuntu 9.10"
date: 2010-05-28
forum: Multimedia Software
---

### Post by danpaluska on 2010-05-28
fresh install of ubuntu 9.10 on a dell latitude d630.

sound output works fine.
plug in a ps3 eye webcam and cheese records video just fine.
but no audio.
go to system, preferences, sound

in the past, when i've had usb webcams with microphones, they showed up on the list of devices under the INPUT tab but they don't show up here. only the internal audio analog stereo.

i also would be fine if the analog mic worked but that doesn't work either. 
tried alsamixer and other various volumes controls and the microphone doesn't seem to be muted anywhere. 

anybody have any tips for me?

i've seen some posts about uninstalling and reinstalling alsa but that makes me a bit nervous cause i'm still pretty new to the linux stuff.

thanks,
dan

also, is there a similar command that will list all input devices?
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by marcottebj on 2010-05-28
It seems like I had far better results after I upgraded to 10.04.  I had trouble getting my cam and mic to work properly with 9.10 as well.  It was buggy.  It seemed to work with some apps, and not others.

---

### Post by no2498 on 2010-05-28
read and install all of what the page tells you to
wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

it comes in a deb file also

---

### Post by iDVB on 2010-08-14
Has anyone managed to get the PS3 Eye microphone working on Ubuntu?
I'm running Ubuntu 10.04 and the cam installed plug and play and "video" works like a dream under skype, guvcview etc. I even see it as an "input device" in System > Prefs > Sound. 

But no sound in Skype and no way to turn it out.

My Prefs:
[http://yfrog.com/ncsoundpreferences004p](http://yfrog.com/ncsoundpreferences004p)

Skype Options: (no other options but what is seen here)
[http://yfrog.com/n2options005p](http://yfrog.com/n2options005p)
[http://yfrog.com/mroptions006p](http://yfrog.com/mroptions006p)

Anyone have ideas?

---

### Post by AKADAP on 2010-08-15
When I was playing with the PS3 camera, I discovered that the camera had to be plugged in at boot to get the sound to work, but I was never able to get the sound to work with Skype.

I finally decided to leave the PS3 camera plugged into the PS3, and got a Microsoft LifeCam Cinema for the PC. This camera's audio works with Skype.

---

