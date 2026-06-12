---
title: "No sound devices?"
date: 2011-01-06
forum: Multimedia Software
---

### Post by MorphMaker on 2011-01-06
I just attempted to purge and reinstall ALSA (and all of it's related packages/utils) after disabling the on-board sound in an effort to use only an M-Audio Delta 1010 as the sole sound device. I've also tried to reinstall Envy24, as well as drivers for the ICE1712 chip...

Now, I have no sound devices. alsamixer tells me there is such file or directory. When I go to  /proc there isn't even an asoundrc file there. 

I don't know what to do. I've spent the last 4 hours looking for a fix, and trying all sorts of things, even the comprehensive sound troubleshooting guide on this forum. Nothing. I got absolutely nothing. Everything goes exactly as the guide states, except after rebooting, and trying aplay -l  and  alsamixer, it says there's nothing installed! any ideas? I have to have a sound, this machine is a DAW and it's not even mine!!!:confused: 


End result I'm looking for is to use the Delta 1010 as the ONLY sound device.

Please please help or the owner of this machine will seriously kill me!!!:shock:

---

### Post by MorphMaker on 2011-01-06
Nobody? seriously? I went step by step through the comprehensive sound solutions guide stickied, to no avail. I then searched the forums for everything I could think of. I'm about just reinstall and see how that goes, I guess.  ):P

---

### Post by lidex on 2011-01-07
Did you install OSS? If you did you need to remove those packages first. Then try this:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by MorphMaker on 2011-01-07
[LEFT]Lidex, I appreciate the help, however, after doing the things you mentioned I tried aplay -l........out reads

aplay: device_list:223: no soundcards found...


Here goes a fresh install! wish me luck!:)
[/LEFT]

---

### Post by lidex on 2011-01-07
Good luck!

---

