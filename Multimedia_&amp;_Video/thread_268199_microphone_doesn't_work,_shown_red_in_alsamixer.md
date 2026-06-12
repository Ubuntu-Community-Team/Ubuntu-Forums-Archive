---
title: "microphone doesn't work, shown red in alsamixer"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by ryu kun on 2006-09-29
I know this issue will sound familiar but I've been searching for a long time but couldn't find any solution yet.

My microphone (which works well in winXP) doesn't work in Ubuntu Dapper. 

```
cat /proc/asound/version
1.0.10rc3.

cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xd2400000 irq 66

cat /proc/asound/devices
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer

cat /proc/asound/pcm
00-00: HDA Generic : HDA Generic : playback 1 : capture 1
```

When I run "alsamixer" in terminal, mic control is shown in red and this apparently can't be changed.

I tried to change my input plugin by "system - pref - multimedia system selector" to Alsa or OSS but no avail...

some related pages which I've read:
[http://www.alsa-project.org/~valentyn/](http://www.alsa-project.org/~valentyn/)
[http://alsa.opensrc.org/Record+from+mic](http://alsa.opensrc.org/Record+from+mic)
[http://alsa.opensrc.org/FAQ036](http://alsa.opensrc.org/FAQ036)
[http://audacityteam.org/forum/thread/2378](http://audacityteam.org/forum/thread/2378)
[http://www.linuxjournal.com/node/8234/print](http://www.linuxjournal.com/node/8234/print)

Please help...

---

### Post by herrspock on 2006-10-09
I installed aumix:

sudo apt-get install aumix

I executed it and set IGain to its maximum. The mic works perfectly now.

(You still has to have Capture to 100% in Alsamixer, and +20dB boost activated)

Hope it is useful for you,

Herr Spock

---

### Post by ryu kun on 2006-10-10
Thanks for the reply.

I executed aumix but there is not IGain there. Only Volume, Line and Mic and all of them already at maximum.

---

### Post by Karnex420 on 2006-10-22
Found this in the description of aumix in the synaptic package manager:  

"The old companion package aumix-alsa, which did take advantage of the
extra facilities in the ALSA sound driver, is no longer available.
This package should work fine with the OSS compatibility layer of the
modern ALSA drivers."

Hope you solve it.  I have the same problem.  I'm afraid my soundblaster 5.1 bought here in Shanghai emu10K1x is causing my problem.  I see my driver but with a different chipset showing on the alsa soundcard matrix list page.

When I disengage my default audio in bios I can't boot up.

We'll get it.

---

### Post by lnxnewbie on 2006-10-24
> **herrspock said:**
> I installed aumix:

sudo apt-get install aumix

I executed it and set IGain to its maximum. The mic works perfectly now.

(You still has to have Capture to 100% in Alsamixer, and +20dB boost activated)

Hope it is useful for you,

Herr Spock

Thanks herrspock,
I've been struggling for a few days now. After installing aumix and set IGain to 50%, skype 1.3 is now working.:-D

---

