---
title: "wine &amp; audio problem"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by kris2pe on 2006-07-31
I have trouble enabling audio on wine!
Coz everytime I click on the audio it crashed & gives me this error!

Creating link /home/tope/.kde/socket-tope-desktop.
can't create mcop directory

So how do I fix this?

---

### Post by RedKrieg on 2006-07-31
There's a post about that here:

[http://www.ubuntuforums.org/showpost.php?p=846165&postcount=7]("http://www.ubuntuforums.org/showpost.php?p=846165&postcount=7")

Just change socket-ubuntu to socket-tope-desktop in the tutorial.

---

### Post by kris2pe on 2006-07-31
thanks after which I get these errors
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)

Now I can access the audio tab! How do I enable the audio? 
Coz I tried enabling Alsa & OSS what are other configuration that I need to enable to make it work?

---

### Post by RedKrieg on 2006-07-31
Well, I can't get any audio in wine either.  You can get rid of the Jack error message by doing:

```
sudo apt-get install libjack-dev
```

I really wish I could get sound using either alsa or oss, but neither work for me.  As for the midi thing...  no idea, but I don't get it (maybe my sound card lacks midi support)

Some people say to try winamp to test sound...  I tried and still get no sound.

Wine 0.9.18

EDIT: I'm using usb audio instead of my onboard soundcard...  are you doing something similar?

---

### Post by kris2pe on 2006-07-31
USB audio? Mine is a sound blaster! Creative Live! Will emulation using Vmware work?

---

