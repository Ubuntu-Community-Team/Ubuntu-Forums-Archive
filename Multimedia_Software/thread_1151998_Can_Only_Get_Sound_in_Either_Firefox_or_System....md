---
title: "Can Only Get Sound in Either Firefox or System..."
date: 2009-05-07
forum: Multimedia Software
---

### Post by Literati on 2009-05-07
Alright, here's my dilemma. 

I installed a new ESI Juli@ soundcard last night for the sole purpose of driving my new Headphone Amp. 

Now, I obviously don't want to listen to my headphones all the time, so I keep my computers speakers hooked up to onbaord sound. 

I need a quick easy way to switch between the device that I want to use. However, I'm finding that when I use on-board audio I can either only get sounds from the system (i.e. Songbird, VLC etc) and not Firefox (Well, to be specific, from Flash.) but then if I switch around some settings and reboot, I get the OPPOSITE, where I get sound only from YouTube, and not from Songbird (I get an Invalid Argument error) 

This isn't the PulseAudio one source bug, or at least it doesn't seem to be.

Anyway, I need these two things to work independently of one another, and to work well. :)

Thank you very much in advance.
Matt

---

### Post by Literati on 2009-05-07
Bump. This is really annoying.

I've tried ALSA, I've tried PulseAudio, but I either only get sound from Flash in Firefox, or from my system like in VLC or something. I just need this all to work, and I can't understand why it isn't.

---

### Post by Literati on 2009-05-08
I'm really willing to try anything. :P

---

### Post by alexandari on 2009-05-08
So you say you are using ALSA? All your sound settings are using ALSA? If it isnt,have you tried it? Here`s a little experiment.
**sudo apt-get install alsa-oss**
after which..
**aoss firefox**
now if your sound is working with both of the applications,then your using oss with something?

---

### Post by technocp on 2009-05-08
Try this out
Use below command lines
sudo apt-get install ndiswrapper-utils
aplay -l
alsamixer 
alsactl store 0
sudo alsactl store 0
aplay
restart

---

### Post by Literati on 2009-05-11
Neither of those have worked. :(

When I try aoss firefox-3.5 it just doesn't open any browser. And technocp's suggestion doesn't work either :(

I followed the Sound Troubleshooting guide, editing my alsabase.conf file and everything and alas, still no luck. :(

Anyone else have an idea?

---

### Post by Chronon on 2009-05-12
No.  Unfortunately I have the same problem.

update:
I followed psyke83's pulseaudio guide and got sound working in both.  I think the problem has to do with obsolete configurations that need to be removed.

---

### Post by Chronon on 2009-05-12
*sorry for double posting.  Moderator can delete this message.

---

