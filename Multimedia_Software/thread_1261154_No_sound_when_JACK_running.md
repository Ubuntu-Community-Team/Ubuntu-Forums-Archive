---
title: "No sound when JACK running"
date: 2009-09-08
forum: Multimedia Software
---

### Post by Joe of loath on 2009-09-08
Hi there

I have a new laptop, a dell inspiron 1545. Although its a little buggy, jaunty works fine. The problem occurs when JACK is started. All sound stops, if I try to open an audio file, totem stays at 0:00, although the caption underneath says 'playing'. if I type  /proc/asound/card0/codec#* | grep Codec I get:
Codec: IDT 92HD71B7X

I can only get jack to run if I force 16 bit sound, and disable realtime. Maybe this has something to do with it?

Thanks in advance
Joe

---

### Post by Joe of loath on 2009-09-08
Ok, I've done a little bit of detectoring, if jack isn't running, the 'test' buttons in preferences->sound work, but if I start jack and try them the applet crashes. If I change alsa to OSS I get a little further, and it gives me this error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

Is this any more help?

---

### Post by Joe of loath on 2009-09-09
Please people, this is rather important!

---

### Post by markbuntu on 2009-09-09
Well, this is a long running sort of involved issue but you can resolve it with a little work on your part.

First, a little background so you understand what exactly in going on. totem and other apps use alsa or the pulseaudio sound server. Jack does not and when it is running will take over exclusive control of the sound hardware. As a result applications trying to use the alsa or pulseaudio sound server will find themselves shut out by jack, thus the error message.

There is a pulse-jack module available with pulseaudio that will allow applications to connect through pulseaudio to jack but, because jack is not in the /main repository this module has been stripped out of pulseaudio for Ubuntu. 

But you can get it yourself and install it and use it. There are directions for doing so near the end of the OP here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you have any problems or questions come back here and we will try to help you.

---

### Post by Joe of loath on 2009-09-09
Thanks, much appreciated! I've had problems like this before, but when I googled this one all the solutions were different...

---

### Post by Joe of loath on 2009-09-10
hmm, seems to work now, thanks for the link though, very useful!

---

