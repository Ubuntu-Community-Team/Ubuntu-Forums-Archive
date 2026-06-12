---
title: "Problem with wine and and other audio programs"
date: 2009-01-09
forum: Multimedia Software
---

### Post by Ketara on 2009-01-09
I've been looking around the forums for a solution to this, and have found several threads in regards to wine and sound, but none of the ones I have found have described my problem exactly, and none of them have been able to fix it.

Here's the deal.

If, when I boot up, the first program I run that has any sort of audio is NOT wine, then if I run wine afterwords wine will not have sound, even after closing the other programs.

If, when I boot up, the first program that I run is wine, then wine will have sound but no other program will have sound, even after closing wine. Further, if I run wine first, and then repeatedly attempt to run other programs with audio (even after closing wine), not only will they not work but it will eventually cause the computer to hang.

The hanging problem will only occur if I run wine first. If I run anything else first I can open and close wine as much as I'd like, it just won't have sound.

I've tried changing my audio mixer around and installing various lib-whatevers that were talked about on a few threads, and none of it has made any change to this issue at all.

I'm running Hardy on an HP dv8000 laptop.
Kernel: 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
Audio card: "nVidia Corporation MCP65 High Definition Audio (rev a1)"
Wine 1.1.8

Any ideas?

Thanks in advance.

---

### Post by markbuntu on 2009-01-09
Try setting wine to use oss and then launch wine with 

aoss wine

or

padsp wine

If that gives you a problem then you are missing the oss wrappers and plugins for alsa and/or pulse audio or some other packages or your sound server is misconfigured.

To fix that, go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Ketara on 2009-01-09
Those two commands did not help.

I installed all the bits on your thread through synaptic, still didn't change anything.

The pulseaudio thread you have linked to in the other thread in regards to wine I simply don't understand.

Re:
Wine ¶

The ALSA output in Wine (beta releases) does not work with the PulseAudio plugin for ALSA (called alsa-pulse) currently, at least not for DirectSound. See this bug report for Wine and this report for PulseAudio.
If it does not work to route the audio through ALSA, perhaps Wine will work better if it uses the OSS or ESD procol between Wine and PulseAudio.

Distributions like Ubuntu 8.04 is set up so that the default ALSA "device" is pulse, i.e. the PulseAudio plugin for ALSA. Furthermore PulseAudio will take control over the hardware to avoid the use of dmix (better latency, less compatible with things like Winealsa).

If a gamer wants lowest possible latency, and does not need any other app to play sound (like voice chats like "Teamspeak"), then they should use pasuspender. This makes PulseAudio release the hardware interface, so a game can use it exclusively, and without dmix or PulseAudio in between.

Winealsa is now ( some time before may 4. 2008) fixed, so it uses the alsa device "default" instead of "default:0" (or like numbers), and does not require a volume control called PCM but uses the default volume control.

Not sure if I'm missing anything, that guide was kind of long ~_~

---

### Post by Ketara on 2009-01-09
Doublepost!

I spoke too soon. Switching the audio back to alsa after installing all those plugins gives me sound in wine after playing a different audio program, but it is extremely choppy.

---

### Post by markbuntu on 2009-01-09
Well, that is progress of some sort. Are you using pasuspender or aoss or padsp when you start wine?

---

### Post by Ketara on 2009-01-10
Okay, update.

No, padsp aoss and pasuspender don't seem to affect it any.

I looked around for threads on choppy sound, found a couple saying to downgrade wine. Downgraded to 1.1.5 like they suggested, didn't affect it any.

---

### Post by Ketara on 2009-01-11
So I was just playing around with different programs in wine and winecfg to see how messing with audio settings changed things, and managed to crash the entire computers audio in a way that looks suspiciously like my hanging problem in the initial post. I figure I just need to reboot (haven't yet because I'm working on some other stuff atm) but I thought I'd post this, because it seems to me that if wine is crashing other programs audio that it can't just be a wine problem.

I think I might just want to go back to my old setup where wine was working so long as I rebooted and then opened it before any other program.

---

