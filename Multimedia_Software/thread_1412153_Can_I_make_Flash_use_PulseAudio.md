---
title: "Can I make Flash use PulseAudio?"
date: 2010-02-20
forum: Multimedia Software
---

### Post by sleepee on 2010-02-20
So i'm wondering if there's a way to make sure that Flash uses PA, since i'm pretty sure it's going directly to alsa, which i believe is the cause of a sound conflict with the rest of my system's sounds.
im sort of pessimistic about this since i know flash is proprietary and it might be hard to tweak with it too much, but any help with a solution or a workaround would be appreciated.. thanx..

btw, i'm running 64 bit ubuntu 9.10 with flash 10 64bit....

---

### Post by sleepee on 2010-02-28
well, this really sucks...
i'm sure i'm not the only one with this problems....and i know that flash is proprietary, but there must be a workaround right??  there's got to be a way to prevent flash from hogging alsa all to itself and locking out other programs from using sound...
i've tried to take out pulse audio, but that doesn't work... so i reinstalled PA again..
i've also made sure i'm using the latest flash version (for 64 bit) and latest alsa version..

so far, the only thing i can do that sort of works is running firefox in a virtual machine..
since virtualbox uses pulse audio, apparently that's the way i can watch flash IN the virtual machine and listen to other sounds in my  system.

---

### Post by Yellow Pasque on 2010-03-01
I guess it's theoretically possible...
It should be installed by default, but you'll need this package:
```
sudo apt-get install libasound2-plugins
```

```
gedit ~/.asoundrc
```
This should bring up a blank text editor window (unless you've previously created/modified the .asoundrc file). Copy and paste this:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```
Save and reboot. Let me know if/how well it works. I don't use PA (or ALSA), so I can't say.

---

### Post by sleepee on 2010-03-01
thanx for the suggestion, but i didn't see any difference.
it worked pretty much the same as before....  in other words, it didn't work..
still have the sound conflict, and flash still apparently won't use flash (assuming that's the reason for the sound conflict)

btw, what does that code actually mean?  especially the pcm and ctl part.... if you don't mind me asking... im just trying to learn as much as i can about ubuntu since i'm somewhat of a noob...

---

### Post by Yellow Pasque on 2010-03-01
> btw, what does that code actually mean? 
ALSA's configuration files make little sense to me. I got it from the following page (which may be outdated): [http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

EDIT: To continue troubleshooting, try starting ffox from the terminal.

---

### Post by sleepee on 2010-03-01
wait it worked!!!
thanks for showing me that page...   the code is working (even though i still don't know exactly what it means), but i just had to put it in /etc/asound.conf instead of the /.asoundrc file.

so i guess i was right.  it looks like flash didn't want to use pulse audio and hogged alsa all to itself, or else didn't play sound at all.. 

but now it works like a perfectly!!  thanks a lot!!!

---

### Post by Yellow Pasque on 2010-03-01
> **sleepee said:**
> (even though i still don't know exactly what it means) ... it looks like flash didn't want to use pulse audio and hogged alsa all to itself, or else didn't play sound at all.. 
It means.. route apps that use ALSA API to the pulseaudio sound server.

> but now it works like a perfectly!!  thanks a lot!!!
Cool. I'll put this in my bag of tricks. Enjoy your sound!

---

### Post by tourette on 2010-05-30
:guitar: YOU ROCK!!! thank you very much i was looking for this for many days. I was sure that flash was using alsa not pulseaudio nor jack and that was the reason i couldnt play any sound on other aplication.

---

