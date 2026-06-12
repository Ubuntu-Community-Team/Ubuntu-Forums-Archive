---
title: "Got TS and ET Working, Finally"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by TrendyDark on 2006-12-03
I have been struggle with this problem since I first got Ubuntu running on my computer, I could never use TeamSpeak and have sound in another application. I'm glad to say, it cost me $40, but I fix my problem.

I bought a Creative Sound Blaster Audigy 4 (non-pro) with my new system and then, after some tweaking, got all my sound options setup and working properly.

The trick is to reorder your sound cards (onboard is always first to a pci-card) in the /etc/modprobe.d/alsa-base file:

```

option snd-emu10k1 index=0
option snd-hda-intel index=-2

```

THe index of -2 pretty much kills off my on-board sound for me.

After that I can run ET and TS with only one added step:

```

sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0p/oss

```

Then my Mic wouldn't work in teamspeak, but after playing with the OSS Mixer and Alsa Mixer a bit, I got my mic working (had to turn on analog mixing in the alsa mixer and the capture options for the OSS Mixer)

I also did this, but I don't know if it helped or not:

```

sudo -i
echo "TeamSpeak.bin 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "TeamSpeak.bin 0 0 enable" > /proc/asound/card0/pcm0p/oss

```

(I did this when I was frustrated with messing with OSS/ALSA sound options, but soon after figured out my problem)

Has anyone else gotten these two programs running together nicely? I read about this problem every day and there seems to be no easy fix for it, other than spending the cash on a upgraded sound card (Which I suggest everyone to do if you haven't gotten your problem fixed, just look for a card in the alsa soundcard matrix that has hardware mixing support).

---

### Post by rejser on 2006-12-03
Didn't do anything, worked direct out of the apt-get. Run both World of Warcraft Through wine (have to start TS before wow though for some reason) and with ET, works great. 
SB live (emu10k1)

---

### Post by TrendyDark on 2006-12-03
Was probably just my mixer settings out of the box that were messed up.

---

