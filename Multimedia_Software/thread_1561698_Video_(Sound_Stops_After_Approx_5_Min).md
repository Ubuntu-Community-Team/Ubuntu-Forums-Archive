---
title: "Video (Sound Stops After Approx 5 Min)"
date: 2010-08-26
forum: Multimedia Software
---

### Post by dowtish on 2010-08-26
Ubuntu 10.04 Standard Installation

When playing video in VLC the sound cuts out after around 5 mins!

Had the same problem with Ubuntu 9.10 but cannot remember the fix!:confused:

All help appreciated!

Soundcard details below:


00:08.0 Multimedia auCM8738
    Flags: bus master, medium devsel, latency 32, IRQ 5
    I/O ports at ac00 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: C-Media PCI
    Kernel modules: snd-cmipci

---

### Post by dowtish on 2010-08-26
Found this in another thread wasn't what I was looking for but seems to work:

> sudo apt-get --purge remove pulseaudio && sudo apt-get install esoundBy the looks of things it removes pulseaudio and installs esound.


I'm only using my computer as a media centre so this is a good work around for me!

Don't know the full implications of what I've done but hell :evil:

Will leave thread open for feedback and the like.

---

### Post by tommcd on 2010-08-26
> **dowtish said:**
> 
By the looks of things it removes pulseaudio and installs esound.
Don't know the full implications of what I've done but hell ...

See post #4 of this thread to properly remove pulseaudio:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273)
You should also remove *gstreamer0.10-pulseaudio* to be rid of pulseaudio.
I did not have to install all that alsa and esound stuff. I just removed pulseaudio and gstreamer0.10-pulseaudio.
You should also run *gstreamer-properties* and set everything to alsa after removing pulseaudio.

Here is good article on controlling pulseaudio, so you can turn it on and off at will:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)

---

