---
title: "PS Eye Ubuntu 10.10"
date: 2011-06-18
forum: Multimedia Software
---

### Post by not_the_messiah on 2011-06-18
Hi All!

Ok, so I want to get my PS3 Eyetoy working as a webcam on my Ubuntu box for use with Skype etc. When plugged in, the camera portion works fine and is recognised immediately. However, I am unable to get the microphone working. It appears to be recognised, but there isn't anything captured from it.

I have removed PulseAudio as it was interfering with my quest to get 5.1 working over HDMI passthrough in XBMC.

I did have it working briefly, but I must have changed something, and now I cannot get it to work for love, nor money!

This is what my system finds:
```
$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: CameraB409241 [USB Camera-B4.09.24.1], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have tried alsamixer -c 1, but that gives me the following error:
```
cannot load mixer controls: Invalid argumen
```

If anyone has any idea at all that could help me, I will be very grateful!!

---

### Post by gordintoronto on 2011-06-18
If you run Sound Preferences, and click on the "input" tab, do you have mutiple choices?

---

### Post by not_the_messiah on 2011-06-19
> **gordintoronto said:**
> If you run Sound Preferences, and click on the "input" tab, do you have mutiple choices?

Hi,

Sound preferences no longer works, which I am assuming is because I have removed PulseAudio. I can select the correct device in gstreamer-properties, but when I do a test, no sound is picked up.

---

### Post by not_the_messiah on 2011-07-19
Finally got this working! I added the following:

> CARDINFO{driver}=="USB-Audio", INCLUDE="usb", GOTO="init_end"


To /usr/share/alsa/init/00main in the section that is '# real ALSA configuration database'

Hope this helps someone :)

---

### Post by mixer3d on 2012-05-14
Hi 
Thank You its works for Audacity... i'm working with skype now ;) testing on 12.04 lts  
greetings

---

### Post by oldos2er on 2012-05-14
Old thread closed.

---

