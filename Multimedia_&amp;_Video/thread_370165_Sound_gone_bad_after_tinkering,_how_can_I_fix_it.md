---
title: "Sound gone bad after tinkering, how can I fix it?"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by silverklyph on 2007-02-25
I'm using Edgy, and I've been trying recently to install a program called MuseScore, a music notation program.  I was able to actually compile the most recent version, but I still got an error when it came to finding ALSA, ("make release" couldn't find it).  According to Synaptics, I had ALSA installed, and it was version 1.0.11, more recent than the required version 1.0.

  Because of this, I decided to download the most recent version 1.0.13 from [www.alsa-project.org](www.alsa-project.org).  I followed what I thought to be a decent step-by-step guide, but on restart, my sound stopped working entirely.  I tried removing the version I downloaded from the website, and reinstalling the most recent Synaptics version of ALSA.  Now the machine fails to recognize any form of audio driver.  I searched for sound troubleshooting guides on the forum  but nothing works.

  sudo modprobe snd- 
     returns "FATAL: Module snd_ not found"

 /proc/sound/version doesn't exist

  When I try to run alsamixer, I get:
     alsamixer: function snd_ctl_open failed for default: No such device

    So my question is, is there a way to get my audio setup back to the way it was before this tinkering without reinstalling Ubuntu?  Thanks.

---

### Post by dmcdante on 2007-02-25
tried alsaconf? haven't looked at it, but it helped lotsa people so far...
modules like snd_ don't exist, i guess you mean something like snd_bla_bla

try lspci and then figure out your sound chipset, then google for that!

regards, dante

---

### Post by silverklyph on 2007-02-25
alsaconf isn't found when i type it in the console... Some quick research shows that it's part of the alsa-utils package, so I'm guessing that it's broken somehow.  Synaptics shows that it is installed and fine.  I think that's important, but I really don't know how to use it.

---

### Post by dmcdante on 2007-04-17
hmm... try reinstalling the alsa-utils package or find /usr/bin/ -name alsaconf!

---

