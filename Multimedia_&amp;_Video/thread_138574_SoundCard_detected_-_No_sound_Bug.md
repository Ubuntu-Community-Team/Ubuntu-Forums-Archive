---
title: "SoundCard detected - No sound? Bug?"
date: 2006-03-02
forum: Multimedia &amp; Video
---

### Post by Dolfhin on 2006-03-02
Hi,

I have a onboard ESS Allegro PCI soundcard which worked fine using windows however I decided to install linux on this box to try it out. Due an unfortanute error my primaire windows box crashed so now i'm forced to make use of this linux box for the time being ;)

First of all, let me say that I'm impressed by the current state of linux, although installing Opera and OpenTTD is a bitch if you do it for the first time it isnt to hard to do a second time ;) And I guess that's true for most linux stuff. 

However being the linux noob as I am I failed to get my sound working. The sound test do not work (as in, no sound) but my sound card is reported. I will be more than happy to provide additional details if required.

edit :
My card is supported : [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-ESS_Technology#matrix) and I'm not the only one with this problem :
[http://www.linuxquestions.org/questions/showthread.php?t=291435](http://www.linuxquestions.org/questions/showthread.php?t=291435)
[http://www.linuxforums.org/forum/peripherals-hardware/43995-little-help-please-sound-card-2.html](http://www.linuxforums.org/forum/peripherals-hardware/43995-little-help-please-sound-card-2.html)

---

### Post by Aewheros on 2006-03-02
Sorry if you've already checked this but...

Sound is muted by default. Double click the sound icon in the upper right corner of the screen. In the mixer window, first enable display of all tracks (Edit>Preferences) then turn the volume up on them all to find the right one, to me it was Analog Front. Also make sure that "SPDIF Out" under the switches tab is unchecked.

---

