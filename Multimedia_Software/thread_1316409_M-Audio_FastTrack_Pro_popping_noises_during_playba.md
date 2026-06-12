---
title: "M-Audio FastTrack Pro popping noises during playback"
date: 2009-11-05
forum: Multimedia Software
---

### Post by chorca on 2009-11-05
Karmic is running great on my system, but I'm having one little issue here with my audio interface.. I have an M-Audio FastTrack Pro, a USB audio interface outside my machine, which I have selected in Sound preferences and plays back audio correctly.

However, during playback of video in both Totem and VLC, I get a random popping noise during the playback. It's not related to the power-down issues, as it occurs constantly during playback, mainly on the left speaker. I've looked around and found some older threads, but they're several versions old and most likely don't apply any longer. I've tried killing PulseAudio with no change.

Not really sure what else to do here..

Any ideas? Anyone else with USB-Audio related noises?

---

### Post by joegiampaoli on 2009-11-06
A little guide I did for the Fast Track Pro under ubuntu linux. Specifically for pro audio. Maybe something there might help you.

[http://www.joegiampaoli.com/blog/?p=462]("http://www.joegiampaoli.com/blog/?p=462")

Cheers!):P

---

### Post by chorca on 2009-11-25
Ran through the whole thing, recompiled a kernel, (staging modules have errors in them, disable the ones that are broke) fixed issues with it not detecting (Seems the 0x before the vid, pid, and device setup are not necessary, and it won't start the module if they're there)

Still popping, during video playback. Just as often as before, and while I may have not noticed it, it seems there are many more smaller pops between both channels. The really loud pops are happening only on the left channel. Anything else I can modify to keep that from happening?

---

### Post by chorca on 2009-12-13
And now it seems the kernel only starts once every two times I try to boot. It hangs before X even starts and pressing ctrl-alt-del restarts, and the next time it starts it seems to run. However, the popping is still there. 

It only happens when video is being displayed. If i start a video, then open a window over top of it, the audio is fine. As soon as I bring the window into the foreground it begins popping again.

Disabling window effects (setting Visual Effects to "None") seems to fix the issue.

---

### Post by JoelBluescreen on 2009-12-23
I do post on this forum because I didn't get any answer from my french forum so sorry to bother but...

I also have a M-Audio Fast Track Pro ([http://www.m-audio.fr/products/en_us/FastTrackPro.html](http://www.m-audio.fr/products/en_us/FastTrackPro.html)) that is recognized by my Ubuntu 9.10 BUT as a single output device.

I would like to use all its I/O.

please find below some useful outputs:
- lsusb : 
...
Bus 002 Device 002: ID 0763:2012 Midiman

- cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec 11 2009 for kernel 2.6.31-16-generic (SMP).

- uname -a
Linux Blue2 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

Can you help with this?

Thanks

---

### Post by frisbee23 on 2010-05-04
i have the same problem and no workaround as of now. first i thought it was a pulseaudio problem, but then i was able to reproduce the popping noises with pure ALSA output. it must be a bug in either the usb-audio module or in ALSA itself.

i considered posting the bug to launchpad, but it will surely get tagged as low priority and won't be fixed.

anyone knows a workaround?

---

### Post by chorca on 2010-05-04
Did you try disabling visual effects in the Appearance panel? That seemed to fix the problem for me.

---

### Post by frisbee23 on 2010-05-04
i  write software (with lots of opengl) that has to be compatible with compiz so metacity is no option here.

and it is beyond me, why changing something about graphics fixes sound problems. magical in a way ;)

---

### Post by joegiampaoli on 2010-05-04
It probably would as a matter of fact! If you graphics card's IRQ level is higher than your USB IRQs killing the potential to your M-Audio card.

---

### Post by chorca on 2011-10-04
Well, I thought I'd resurrect my dead thread, because this is still happening. Posted this a year ago and there are still issues with the Fast Track Pro. Fresh install of 11.04 and it's still popping all the time. Disabled effects, using Ubuntu Classic desktop (no effects) at login, and when I open or close windows, or do anything regarding visuals, I get loud and soft pops in the speakers while I do. Restarted pulseaudio and such, still having problems.

Anyone else having these issues? Is there a way I should file a bug report regarding this hardware? Should I dump plain Ubuntu and start installing Ubuntu Studio?

---

### Post by joegiampaoli on 2011-10-04
You probably want to read my new blog, I explain there why I no longer use ubuntu for "pro audio"

[http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html](http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html)

---

