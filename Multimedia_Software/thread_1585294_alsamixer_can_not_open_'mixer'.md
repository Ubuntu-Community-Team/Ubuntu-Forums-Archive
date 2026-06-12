---
title: "alsamixer can not open 'mixer'"
date: 2010-09-30
forum: Multimedia Software
---

### Post by BelowGrade on 2010-09-30
Ubuntu Server Edition 10.04, a headless server machine that (among other things) is my music server, running mpd.   The hardware uses an Intel HD audio interface.   Sound works, but the output level is very low both with mpd and with mplayer.   So I go to run alsamixer to see if there are some adjustments I can make.

> ~> alsamixer
cannot open mixer: No such file or directory

Indeed, there is no /dev/mixer.  But /dev/snd/controlC0 exists.   I have no ~/.asoundrc file, nor an /etc/asound.conf file.

---

### Post by SlugSlug on 2010-09-30
may sound daft but have u installed alsa?

---

### Post by BelowGrade on 2010-09-30
Sound does indeed work.   Just too soft.
I created a simple /etc/asound.conf and now alsamixer starts up, but it does not make the playback level any higher, even though all the sliders are up.

If I feed the LineOut signal into my amplifier's "Phono" input I get reasonable levels, but the RIAA equalization is all wrong..

---

### Post by SlugSlug on 2010-09-30
Not to sure -- my sound problems are always fixed with

apt-get remove pulseaudio

and 

apt-get install alsa

but thats due to crap sound quality  when I use pulse

---

### Post by BelowGrade on 2010-09-30
Fortunately, pulseaudio was never installed in the first place.   This is a Server package.   Alsa was there, and I added the alsa-utils.

---

### Post by BelowGrade on 2010-09-30
Problem solved.   Turning up the "Front playback" gain made the sound level from the Back Panel playback jack get louder.  (??)

---

### Post by atentik on 2011-03-07
> **BelowGrade said:**
> Sound does indeed work.   Just too soft.
_I created a simple /etc/asound.conf_ and now alsamixer starts up, but it does not make the playback level any higher, even though all the sliders are up.

If I feed the LineOut signal into my amplifier's "Phono" input I get reasonable levels, but the RIAA equalization is all wrong..

Unfortunately, I am having the same problem. How did you created the /etc/asound.conf? What are the contents of that file?

---

