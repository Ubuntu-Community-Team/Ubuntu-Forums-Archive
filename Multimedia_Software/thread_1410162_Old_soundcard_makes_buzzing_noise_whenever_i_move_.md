---
title: "Old soundcard makes buzzing noise whenever i move mouse, clik, type"
date: 2010-02-18
forum: Multimedia Software
---

### Post by abben on 2010-02-18
I hope the bolding and underlining makes it reader friendly.

_The problem:_
Basically, whenever there is some data-crunching of any kind, I hear it in my speakers, as a buzzy or prickly sound. If I just listened through my speakers and looked away while someone else was at the computer, I could tell when they were moving the mouse or launching a program based on the sound.

_My sound device(s):_
The sound device for this system is super old: it is a Crystal CS4235 which I believe was made in 1998. It is part of the Delphi-III mainboard on an old etower 333k. I have a sound blaster card to the side that I might install if I get desperate.

_How I got sound working_:
 I did a minimal, bare-bones installation. I originally had **no** sound related programs or drivers of any kind.

To set up my sound, I did this:

```
sudo apt-get install **alsa-oss alsa-utils oss-compat**
```

I used my newly installed modprobe tool:

```
sudo modprobe **snd-cs4236**
```

I went to my newly installed **alsamixer**, and unmuted everything and turned up the volume on everything. I installed vlc, since vlc plays everything. Lastly added snd-cs4236 to the bottom of /etc/modules.

And now I'm here, with working, but crackly sound. It's not just that I'm using an old soundcard is it?

---

### Post by abben on 2010-02-18
Bumping. Maybe I'm just asking for too much out of an old computer? As an expression of thanks, I leave you with this picture of david foley.

---

### Post by abben on 2010-03-02
Hooray I "solved" it by installing a soundblaster card instead. So anyone out there who also has this problem, you know what to do! blues cluuu-ues blues clues!

---

