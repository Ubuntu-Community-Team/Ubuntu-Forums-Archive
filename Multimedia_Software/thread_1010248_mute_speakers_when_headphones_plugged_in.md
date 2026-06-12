---
title: "mute speakers when headphones plugged in"
date: 2008-12-13
forum: Multimedia Software
---

### Post by slymi2005 on 2008-12-13
Wondering if there is an easy way to mute sound on my desktop when my headphones are plugged in?

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by tigerstripedcat on 2008-12-13
I don't think it would be easy.  Usually you'll see this feature on laptops and it's the hardware telling the speakers to shut off if a headphone is pluged in.  You should google for an easier way.  But if you want

_Hit a few buttons_
Call up a mixer (kmix if in kubuntu) and hit the mute on the speaker and unmute the headphones.  You can make a shortcut icon to make this faster

_Hit a single button_
Look into amixer commands, you can control your mixer from the command line, then make a small script which runs two amixer commands: one to mute the speakers, and one to unmute the headphones, then you can assign this script to a key on your keyboard via gnome/kde keyboard setup

_Hit no buttons_
Here you would have to activate a script on a kernel event (detection of headphones plugged in)  This would be rough, but there might be a program that does this.  Like I said you'll probably have to google some more.
TSC

---

### Post by slymi2005 on 2008-12-14
Alright so my monitor is connected using an hdmi cable, I read somewhere that it is not possible to mute the speakers because of this, so is it hopeless?

---

### Post by tigerstripedcat on 2008-12-22
Well if you can't mute the speakers AT ALL then it might be, but can you even turn down the volume on the speakers while still hearing stuff through your headphones? Open up your mixer (gmix? I use kmix) and make sure you go to the options and check all the boxes so that you are trying every single setting.

---

