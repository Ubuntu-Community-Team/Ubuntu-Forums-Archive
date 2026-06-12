---
title: "Sigmatel 92xx playback through MIC"
date: 2008-08-29
forum: Multimedia Software
---

### Post by quazi on 2008-08-29
So I'm running a Dell m65 Precision with a Sigmatel STAC9200 chipset with Hardy Heron.  I want to be able to run my Wii's audio through my mic port as I was in windows.  Thus far I've been unsuccessful.

I've followed the directions given here: [http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200](http://ubuntuforums.org/showthread.php?t=201887&highlight=dell+inspiron+SigmaTel+STAC9200)
by adding ```
options snd-hda-intel model=ref
``` to /etc/modprobe.d/alsa-base

Unfortunately that did nothing.  I've checked all the input modes under volume control preferences and still haven't managed to hear anything through the MIC.

---

### Post by quazi on 2008-08-29
I've heard using OSS 4 is a possible alternative, would that have the potential to solve this issue?

---

### Post by quazi on 2008-08-31
The Sound system in linux is definitely a weakspot in my knowledge, so any help that could be provided would be greatly appreciated.

---

### Post by quazi on 2008-09-03
Well, looks like I'll be stuck switching speaker cables back and forth until Intrepid.

---

### Post by quazi on 2008-11-07
Intrepid unfortunately hasn't fixed anything, the MIC still doesn't work (and I've made sure it's unmuted).

---

### Post by Ikith on 2008-11-07
I have the same problem with my mic port on a Gatway thats running stac9250 front mic does not work at all.

---

### Post by quazi on 2008-11-10
Ok, this probably isn't the best solution, but I became frustrated enough to try OSS4.1.  After a lot of finagleing (and in the process getting annoyed enough to switch back to PS/ALSA and failing to do that), I managed to get line-in working.

If you choose to go this route, I recommend following this guide (although I don't know how to reverse what you do) [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Running ossxmixer gives you a meaningless menu of gibberish.  However, if you fiddle around with it enough, things end up working.  If you're interested, I can post an image showing how I have mine set up.

---

