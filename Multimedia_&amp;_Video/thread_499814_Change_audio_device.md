---
title: "Change audio device?"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by ar1stotle on 2007-07-13
OK, I just got a Logitech Easycall speakerphone, and I want to make it my default sound device. However, Ubuntu keeps wanting to output to my onboard sound. I want the Easycall to be the default device because really, my windows sound card is an x-fi which has no linux support, so to use my onboard sound i have to move all the wires around. 

Any help is appreciated!

---

### Post by kevinlyfellow on 2007-07-13
the program gnome-sound-properties has a drop down box so you can select the device you wish to use.  Does that work?

---

### Post by ar1stotle on 2007-07-13
Hmmm... just tried it again. It does seem to work. I guess I didn't notice it the first time cuz the volume was so low.

But for some reason, things like youtube keep playing through the onboard sound card. Maybe it'll work after a restart. Only other thing is that the volume up/down on the speaker still change the master for the onboard.

---

### Post by kevinlyfellow on 2007-07-13
That may be because the flash plugin for linux, although its a nice gesture from adobe, is not that great.  I remember the flash 7 days (not so long ago really) when in order to play a flash video, you needed to stop all programs that use sound from running, then start your browser, then use flash.  In order to allow other programs to make sound, you needed to make sure that flash wasn't running anymore (and closing your browser), and then fire up the noise generating app.  This was due to a long history of not having appropriate audio mixing, but when those days were done, flash was well behind the times.  Flash 9 does allow audio mixing, but if it handles audio anything like its predecessor, then it assumes a lot about your audio system and will not integrate well into a linux desktop.

You may consider using gnash, which attempts to replace flash, but is open source.  It has support for youtube now, but I don't know from experience how it works.

There still may be a way to fix this, hopefully someone knows better than I do.  Perhaps it is something as simple as making a link to the desired device.

---

### Post by kevinlyfellow on 2007-07-13
Out of curiosity, can you list your audio devices?
```
ls -l /dev/audio*
ls -l /dev/dsp*
```

A fun thing to do with these devices btw is to cat put files into them, for instance
```
 cat /etc/X11/xorg.conf> /dev/dsp
```
will let you hear you xorg.conf file.

---

### Post by ar1stotle on 2007-07-16
aristotle@Tsunami:~$ ls -l /dev/audio*
crw-rw---- 1 root audio 14,  4 2007-07-16 17:21 /dev/audio
crw-rw---- 1 root audio 14, 20 2007-07-16 17:21 /dev/audio1
aristotle@Tsunami:~$ ls -l /dev/dsp*
crw-rw---- 1 root audio 14,  3 2007-07-16 17:21 /dev/dsp
crw-rw---- 1 root audio 14, 19 2007-07-16 17:21 /dev/dsp1

Flash still just wants to play over my onboard sound :-/

---

### Post by kevinlyfellow on 2007-07-17
> **ar1stotle said:**
> aristotle@Tsunami:~$ ls -l /dev/audio*
crw-rw---- 1 root audio 14,  4 2007-07-16 17:21 /dev/audio
crw-rw---- 1 root audio 14, 20 2007-07-16 17:21 /dev/audio1
aristotle@Tsunami:~$ ls -l /dev/dsp*
crw-rw---- 1 root audio 14,  3 2007-07-16 17:21 /dev/dsp
crw-rw---- 1 root audio 14, 19 2007-07-16 17:21 /dev/dsp1

Flash still just wants to play over my onboard sound :-/

I bet if you can find a way to change /dev/audio1 to be called /dev/audio it would solve your problems.  I'm looking into how that can be done

Now can you give me lsmod?  I think we need to edit /etc/modprobe.conf (although I don't seem to have it on my system, maybe we need to create it?) to do this

---

