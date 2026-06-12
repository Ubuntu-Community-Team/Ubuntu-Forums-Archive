---
title: "sound card drivers???"
date: 2009-09-03
forum: Multimedia Software
---

### Post by fozbolt on 2009-09-03
is there a program that will allow me to adapt apple sound drivers to work with ubutnu??

---

### Post by fozbolt on 2009-09-03
ubuntu*

---

### Post by Yellow Pasque on 2009-09-03
No, there's no wrapper for audio drivers. What is your issue?

---

### Post by fozbolt on 2009-09-03
well i have the new macbook and i havent had sound since i put linux on here and i was wondering if there was some way for me to get the sound to work without having to pull the case off and manually change which slot my soundcard is in or whatever. i just found a bunch of the recording software and really wanted to get to using it. like i apparently have 4 different kinds of mixers already downloaded but no matter what i try to do i cant get any sound out of it and ive already spent ALOT of time looking for driver updates and everything and i cant find anything. if you need more specific information on my laptop then i can give it to you.

---

### Post by Yellow Pasque on 2009-09-03
> spent ALOT of time looking for driver updates and everything and i cant find anything.
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Please post output of:
```
aplay -l
```

---

### Post by fozbolt on 2009-09-03
heres the output.

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Yellow Pasque on 2009-09-03
You need to upgrade to the latest ALSA (1.0.21) because it has this fix:
>     - ALSA: hda - Improved MacBook 3,1 support 
    This patch adds support for MacBook 3,1 sound by adding a model
    "mb31" with the appropriate init verbs, mixers and channel modes to 
    the ALC883 configuration.

Get the script from the thread I linked to in my last post. Before you run it, you need to edit this part (change the bolded lines)

```
alsa1020 () {
**DRIVER=alsa-driver-1.0.21**
FIRMWARE=alsa-firmware-1.0.20
[B]LIB=alsa-lib-1.0.21
PLUGINS=alsa-plugins-1.0.21
UTILS=alsa-utils-1.0.21
TOOLS=alsa-tools-1.0.21[/B]
OSS=alsa-oss-1.0.17
}
```

Now follow the directions in that thread to run it. After it finishes, one more step is needed:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line:
```
options snd-hda-intel model=mb31
```
Save the changes and restart your system.

---

### Post by fozbolt on 2009-09-03
i already ran the unedited upgrade. and now when i try to run the edited one it wont work. i thought that seeing as how it took you so long to reply, that you were expecting me to run the unedited one and so i did. but now in hindsight i see i should have been more patient. whats worse is that i didnt make a backup. is there anyway to fix this?

---

### Post by Yellow Pasque on 2009-09-03
You can use the script's -r option to "reset" back to the Ubuntu ALSA packages. Then try the edited script.

> i thought that seeing as how it took you so long to reply, that you were expecting me to run the unedited one and so i did. but now in hindsight i see i should have been more patient.
Yeah, unfortunately I'm not paid to do this, so I'm not at your beck and call. Sorry about that :P

---

### Post by fozbolt on 2009-09-03
thanks. i was wondering if i would be able to or not. and i figured as much so its all good. no worries :)

---

### Post by fozbolt on 2009-09-07
so i def did exactly what you said and it still isnt working.

---

