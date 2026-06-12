---
title: "Only MythTV outputs sound through HDMI - why?"
date: 2009-03-01
forum: Multimedia Software
---

### Post by mortenbreumcouldnotregist on 2009-03-01
I have a Gigabyte motherboard with a 780G chipset.
I installed the Catalyst 9.1 drivers and got audio through HDMI in mythtv by entering ALSA:plughw:1,3 as Audio output device - and that is very satisfying indeed.
However, I would also like to have audio from other programs, e.g. youtube on firefox, out through the HDMI cable, but that seems harder for me.
I am able to do a 'speaker-test -twav -d plughw:1,3' and get audio.

I tried installing asoundconf-gtk and used that to set the default card to HDMI, but that didn't help me much, and I don't quite understand why.
After setting the default card to HDMI, my .asoundrc.asoundconf file starts with
```
!defaults.pcm.card HDMI
defaults.ctl.card HDMI
```

When I do a speaker-test without arguments, I get:
```
host:~$ speaker-test 

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Channels count (1) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```

Why is that?
/Morten

---

### Post by mortenbreumcouldnotregist on 2009-03-03
Perhaps speaker-test does not respect the settings made by asoundconf?
Anyone?

---

### Post by mortenbreumcouldnotregist on 2009-03-04
Now I tried 
speaker-test -c 2 -twav
and got sound fine..
Now the question is: How do I set the -c 2 as default, so firefox and pidgin knows that it should be two channel output?
/Morten

---

### Post by daveisfera on 2009-04-02
I am having this same problem, but it appears that everything except for Firefox is playing sound just fine. Any ideas on how to fix this?

---

