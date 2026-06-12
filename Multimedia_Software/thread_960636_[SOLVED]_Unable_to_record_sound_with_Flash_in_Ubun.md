---
title: "[SOLVED] Unable to record sound with Flash in Ubuntu 8.10"
date: 2008-10-27
forum: Multimedia Software
---

### Post by patrickballeux on 2008-10-27
Hi,

In Ubuntu 8.04, I was able to record sound and video using the Flash player version 10.  Flash was connecting directly to the pulseaudio server and it was working great.

Note that all my setup is configured to use the pulseaudio server.

I upgraded to Ubuntu 8.10 over the week-end, and I found out that Flash 10 is not using the "Alsa playback" when playing thru the pulseaudio server and when trying to record sound, I can see the "Alsa recording" from the npviewer.bin, but nothing is actually recorder.

Sound input is working as I can monitor the sound level with Volume Meter of pulseaudio.  This setup was working well in 8.04.

And yes, I tried the .asoundrc and using asoundconf-gtk setting everyting to pulseaudio.

Ah also, my setup is AMD64 but I had similar problems with my other setup Ubuntu 8.10 32bits.

On my 32bits setup, I removed all pulseaudio and I was able to record sound again.  Did the same thing in AMD64, but could not make it work.

I know that Flash 10 supports pulseaudio directly, but it keeps using the ALSA plugin and that seems to be the problem

How can I force the Flash player to use the pulseaudio instead of using the Alsa plugin?

- Did set System - Preferences - Sound to pulseaudio
- gstreamer-properties to puslseaudio
- asoundconf-gtk to pulseaudio
- tried .asoundrc to default to pulseaudio

If I remember well, in 8.04, the asoundconf-gtk was the key to make Flash use the pulseaudio or the Alsa plugin.  It does not work in 8.10...

Thanks

---

### Post by patrickballeux on 2008-10-27
Update:

I tested on my Averatec Laptop 3200 (32bits) with a Via sound card (don't remember the model).

I remembered removing everthing about pulseaudio when I first upgraded it because the microphone was not working.  But once the pulseaudio removed, everything was working with Flash 10.

So, I validated the it was working, reinstalled everything for pulseaudio, rebooted and now I have the same problem as my Dell 1521 (HDA sound card).  I then removed completelty pulseaudio, rebooted, double-checked that everything was set to ALSA and still not microphone working with Flash.

Also, I found out that all my inputs are muted and I cannot unmute them (I unmute, close, open, muted again...).  I have this problem on both laptops with Ubuntu 8.10.

I must say that the Averatec was upgraded a few days ago and the Dell was upgraded last week-end.  So I had to update the Averatec because there was a lot of updates to apply.  Did the problem appear with the updates?  

So it is not hardware related, nor driver related.  It seems to involve pulseaudio and Alsa.  And even removing completely pulseaudio is not enough, something is left behind or there is a bug in the last update of 8.10...

Can you confirm this? or have a workaround?

---

### Post by patrickballeux on 2008-10-28
I finally found a workaround:  kill pulseaudio, set sound preferences to autodetect, set capture to your hardware sound card (Alsa or OSS).

It is working but you loose the pulseaudio mix feature.

On the 32 bits laptop, I installed jackd and the libasound-plugins for jack (had to recompile the plugins just to get the jack plugin).  I defined my default alsa card as the jack sound server and Flash could record/play using jackd instead of pulseaudio.

On the AMD64, I was not able to do that because Flash is 32 bits and even if I put the 32 bits jack plugin in /usr/lib32, it would not work.  (Probably I would need a 32 bits jackd installed...).

So on AMD64, I am force to used ALSA only but on the i386, I can replace totally pulseaudio by jackd...

When is the Flash for 64 bits coming out? :lolflag:


Now, I have to wait for the Ubuntu team to follow on the bug report that I made: [https://bugs.launchpad.net/ubuntu/+bug/290121](https://bugs.launchpad.net/ubuntu/+bug/290121)

Have a nice day!

---

