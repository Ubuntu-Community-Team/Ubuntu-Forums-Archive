---
title: "Choppy sound on 12.04 (using logitech z305). Any hints?"
date: 2012-05-29
forum: Multimedia Software
---

### Post by abw123 on 2012-05-29
Hi,

I'm running 12.04 on an ARM based system (Beaglebone), Kernel:[ 3.2.0-psp1]("http://elinux.org/BeagleBoardUbuntu#Demo_Image").
I connected it with external USB speakers (logitech z305, playback only).
The speakers are recognized as a soundcard, but the sound quality is poor. The playback of mp3s (using command-line tools like mpg123) is choppy, stuttering and I can hear occasional pops/cracks.

The full output of the alsa-info.sh script is here:
[http://www.alsa-project.org/db/?f=8e05b7050d95ed41e4039ad81f6a8b049529cc0a](http://www.alsa-project.org/db/?f=8e05b7050d95ed41e4039ad81f6a8b049529cc0a)

The only thing I found so far, is the that the ALSA driver version (1.0.24) doesn't match the Library version (1.0.25). I added the [ppa:ubuntu-audio-dev/ppa repository]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules"), but it doesn't provide a newer version for my kernel. Before compiling it myself (and most possibly break a few things here and there) I would like to evaluate if it is worth the effort.

I also found [this on askubuntu.com]("http://askubuntu.com/questions/138266/distorted-choppy-audio-in-precise") and the solution suggests, that I should play with the module parameters. Some guides suggest to compile a newer kernel instead.

Any hints?
thanks,
Armin

---

### Post by abw123 on 2012-06-05
> **abw123 said:**
> Some guides suggest to compile a newer kernel instead.

It turned out to be a kernel related and hardware specific issue. The culprit was the DMA USB support. kworker was consuming all the resources during mp3 playback.

---

### Post by rabarrett on 2012-06-12
So how did you solve this?  I'm having the same choppy sound on a USB soundcard (Bose).

---

### Post by kamelalohimara on 2012-06-12
displaced

---

### Post by rabarrett on 2012-06-30
I could use help on this same issue too, please.  How did you solve it?

---

