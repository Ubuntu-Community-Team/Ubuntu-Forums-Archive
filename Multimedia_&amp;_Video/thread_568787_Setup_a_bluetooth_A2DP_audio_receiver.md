---
title: "Setup a bluetooth A2DP audio receiver?"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by trapperjohn on 2007-10-06
I would like to know if it is possible, to set up a linux box as a receiver for A2DP bluetooth audio? 

I only found solutions to use a bluetooth headset from Linux but not the other way - connect a bluetooth device (like a cellphone or another PC) to the Linux box and stream music to it.

---

### Post by alephsmith on 2007-10-27
I have been looking for the same option. I would like to set up my Gutsy box to receive audio from my laptop so I can pipe through sound on single set of speakers.

I would settle for an sco receiver in leiu of a2dp.

Please post back here is you find a solution as I have subscribed to this post.

---

### Post by cow_racer on 2007-11-01
> **trapperjohn said:**
> I would like to know if it is possible, to set up a linux box as a receiver for A2DP bluetooth audio? 

I only found solutions to use a bluetooth headset from Linux but not the other way - connect a bluetooth device (like a cellphone or another PC) to the Linux box and stream music to it.

How did you do it?  Are you using Gutsy?

---

### Post by trapperjohn on 2007-11-02
I didn't try it, because I don't own a bluetooth headset. But I remember there is a (beta) ALSA driver for bluetooth called snd-bt-sco.

---

### Post by zonyl on 2007-11-12
I would like to do the same thing within Gusty.  Anyone know if this is possible?

Found this, but it is dated.

[http://www.holtmann.org/linux/bluetooth/audio.html](http://www.holtmann.org/linux/bluetooth/audio.html)

Newer:
[http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

---

### Post by avsa242 on 2008-01-04
I've also been looking for a way to do this...I came across a site earlier this year (it may possibly have been one that zonyl posted - not sure) which had on it source for a program that does (or is supposed to) similiarly what we're looking for. I tried it with my Motorola Razr and it just *barely* did something. When it was running, I could press a number on the keypad and rarely would hear just a blip of DTMF tones on my laptop, or I could hear bits and pieces of audio from a call in progress once in a great while. I will try to find the source on my computer...I still have it somewhere; it was GPL, iirc.

Cheers,
Jesse

p.s. I saw reference on a site that mentioned, "If you want your computer to act like a headset/handsfree to a cellphone, check here," which linked to gammu's site. Now, I've looked high and low on their site and even asked (however got no response) but I've seen no mention of such a capability in gammu.

---

### Post by trapperjohn on 2008-01-05
> **avsa242 said:**
> 

p.s. I saw reference on a site that mentioned, "If you want your computer to act like a headset/handsfree to a cellphone, check here," which linked to gammu's site. Now, I've looked high and low on their site and even asked (however got no response) but I've seen no mention of such a capability in gammu.

That was also one of the first links I've found and I even installed it but couldn't find such a feature in this tool :-(

---

### Post by avsa242 on 2008-03-15
Hopefully those interested have subscribed to this thread. In case you hadn't found what you were looking for (if you have, please share!) I found the sources I was talking about. They appear to use SCO, not A2DP, but perhaps the right person could use it as a basis to change it to A2DP. The author's name is Simon Vogl. I think he may have abandoned the project (or if he hasn't, the newer stuff either isn't publicly available or he's moved it somewhere else) because IIRC, the page these were on said the latest version was from 2004.
Anyway, I have the sources if anyone wants them, but they may be irrelevant now. I found a nice thread on mp3car.com, which I am reading right now. You may want to read it instead:

[http://www.mp3car.com/vbulletin/linux/96013-bluetooth-woes.html](http://www.mp3car.com/vbulletin/linux/96013-bluetooth-woes.html)

Cheers,
Jesse

---

