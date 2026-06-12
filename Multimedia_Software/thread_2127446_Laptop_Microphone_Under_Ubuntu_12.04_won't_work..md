---
title: "Laptop Microphone Under Ubuntu 12.04 won't work."
date: 2013-03-20
forum: Multimedia Software
---

### Post by gregoryshock on 2013-03-20
I don't understand why my laptop microphone won't work under Ubuntu 12.04.  I found this thread [http://ubuntuforums.org/showthread.php?t=780805](http://ubuntuforums.org/showthread.php?t=780805) but I noticed that It's an old thread dating back in 2008.  I'm curious if anyone could give me some ideas where I should start trouble shooting my microphone?

---

### Post by mike acker on 2013-03-20
> **gregoryshock said:**
> I don't understand why my laptop microphone won't work under Ubuntu 12.04.  I found this thread [http://ubuntuforums.org/showthread.php?t=780805](http://ubuntuforums.org/showthread.php?t=780805) but I noticed that It's an old thread dating back in 2008.  I'm curious if anyone could give me some ideas where I should start trouble shooting my microphone?

I have found Google to be the best approach to Problem Solving:

a little google searching turned up this: which is the place to start: make sure Linux is finding your Sound Card

[URL="https://wiki.ubuntu.com/Audio/HDAGeneric"]https://wiki.ubuntu.com/Audio/HDAGeneric
[/URL]
if Linux is finding your sound card then proceed with some basic checking outline here

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) 

*** proceed with caution \ avoid the outdated stuff ***

---

### Post by gregoryshock on 2013-03-23
I decided to plug in an external Microphone It seems that the External Microphone works, but Linux isn't finding the built in one.

---

### Post by pbrane on 2013-03-24
have you installed pulseaudio volume control? You should be able to see your microphone and set the input levels with that.

```

sudo apt-get install pavucontrol

```

... should get the program you need. If the mic doesn't show up in there, I don't know what to do next. I've had issues with the internal mic being turned off and/or levels being very low.

---

