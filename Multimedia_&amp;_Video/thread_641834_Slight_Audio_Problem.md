---
title: "Slight Audio Problem"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by mikeyr71730 on 2007-12-15
I've installed Ubuntu 7.10 on my MacBook Core Duo, and I love it.  I have only two problems, and one has to do with the audio (I'll discuss the other in the appropriate place).

When I play any sort of sound, there's a slight popping noise in the background.  This happens with headphones and the built-in speakers.  It has the faint resemblance of playing a slightly scratched record.  The sound doesn't completely cut out at any point, but it pops all the time.

I've done a little research, and I can't come up with any solid evidence as to what the problem could be.  I thought maybe the low latency kernel would fix this, but I don't want to sacrifice battery life for a low latency kernel.

Is this a driver issue?  If not, what could it be?  I'm willing to wait for a fix if I have to.  The problem isn't severe.  It's just annoying.

---

### Post by Ripfox on 2007-12-15
make an .openalrc file (with gedit text editor or something similar) in your home directory and past exactly this:

(define devices '(native))

into it and rebooting...no idea why it works but it fixes all my games that had scratchy audio.

Hope this helps folks

Ripfox

---

### Post by mikeyr71730 on 2007-12-27
After fighting with college midterms and family emergencies, I've finally found time to try this solution and can say that it doesn't seem to be affecting my audio output in any way.  I've done a little research, and I've tried a few variants of this code.  I cannot seem to fix this problem with an .openalrc file.

My problem isn't specific to games -- it spans the entire system.  If I play a sound in any application (whether it's using ALSA or OSS or OpenAL), it's choppy and scratchy (though games using OpenAL seem to exhibit this problem a little more noticeably at times).  More specifically, only the left channel is choppy/scratchy.  The right channel is fine.

Does anyone have any more suggestions?

---

### Post by mikeyr71730 on 2007-12-31
I've fixed the problem by adding "options snd-hda-intel position_fix=1 probe_mask=1" (without quotes) to /etc/modprobe.d/options.  Thanks for all the help.  :)

---

