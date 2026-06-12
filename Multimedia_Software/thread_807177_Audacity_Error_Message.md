---
title: "Audacity Error Message"
date: 2008-05-25
forum: Multimedia Software
---

### Post by condawg on 2008-05-25
Whenever I try to playback any audio on Audacity, I get the following error message --

> Error opening sound device. Please check the output device settings and the project sample rate.

Any ideas why this is happening & how to fix it?
I've been trying some stuff, but none of it had any results.
Thanks =]

---

### Post by xc3RnbFO8P on 2008-05-25
I not sure, but I think you have to change 
sample rate 44000 to 48000 or 48000 to 44000
Edit> perferences> Quality

---

### Post by FuturePilot on 2008-05-25
Are you using PulseAudio?

---

### Post by condawg on 2008-05-25
@Rinky
I can't do a range of sample rates, also I've tried various ones to no avail.

@FuturePilot
No, never heard of it.

---

### Post by rab4567 on 2008-05-26
You might want to try:

sudo apt-get install alsa-oss

In audacity goto edit> preferences> audio i/o select oss:/dev/dsp in playback devises then select alsa default in recording devises. Hopefully this should work but you never know

---

### Post by nlz on 2008-05-26
ctr + p (preferences)
select alsa or JACK

---

### Post by rab4567 on 2008-05-26
I tried Jack the sound quality was horrible but one never knows my current problem is audacity some how changed  the settings in the play back devises. All the playback options are decreased to:

ALSA: iec958
ALSA: spdif
ALSA: HDA Nvidi: ALC88 Digital (hwO,1)

Before(working nicely) After(no sound)
Please help thanks.

---

### Post by paulhelfenstein on 2008-06-25
In your top level user directory, check the file

.audacity

and see if the parameter

PlaybackDevice=

is blank (as above) or not set to any device on your system.  In my case, I had to manually edit the .audacity file and set

PlaybackDevice=/dev/snd

(this was appropriate for my system, but you may have a different device defined on your system).

---

