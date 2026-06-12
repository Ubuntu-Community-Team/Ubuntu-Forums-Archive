---
title: "simultaneous analog and digital output?"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by James79 on 2007-11-25
Well I finally joined the modern world and bought myself a home theatre receiver.

I have a MythTV htpc (Ubuntu 7.04) that currently outputs audio thru my crappy tv speakers (analog). Simply put, I would like to preserve that setup and *also simultaneously *output thru s/pdif at the same time.

I tried putting "pcm.!default spdif" in ~/.asoundrc and that does indeed enable PCM out via digital, but completely disables the analog output.

My motherboard is an Asus M2NPV-VM, and I'm using the onboard soundcard (which uses the snd_hda_intel driver).

Is this even possible? I don't really feel like writting a script to toggle between the two... And I haven't even gotten to AC3 pasthru yet :-|

[edit]
I should clarify, that it is not "MythTv audio" that I'm interested in outputting. I use this machine mostly for [Super] Nintendo emulation (fceu/zsnes), and movies (mplayer) - some of which are stereo mp3 and others which are real DVDs with ac3 soundstracks. It is the output of these that I need to output both over analog and digital.

Thanks!

---

### Post by James79 on 2007-11-28
Anyone? :(

---

### Post by James79 on 2007-12-02
Anyone at all?

---

### Post by kioftes on 2007-12-02
[http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF](http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF))

Just using the gnome alsa mixer as described in the above link worked fine for me!

---

