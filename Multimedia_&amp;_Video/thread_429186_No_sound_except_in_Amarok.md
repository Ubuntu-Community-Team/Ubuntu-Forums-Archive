---
title: "No sound except in Amarok?"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by sirlancelot on 2007-05-01
I upgraded to Feisty from Edgy. Using the default kernel and everything, no custom built apps. Sound worked before upgrade to Feisty. Here's the weird issue: Sound in KDE isn't working, sound in Firefox isn't working. HOWEVER, I can play music in Amarok.... :confused:

```
$ cat /proc/asound/modules
 1 snd_emu10k1
 2 snd_via82xx
```I have two soundcards, I want to use snd_emu10k1 as my primary card. I've followed the "[Comprehensive Sound Problems Solutions Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")" and everything passes... My best guess is that KDE is not selecting the correct primary soundcard. however, I plugged in headphones to my other card and nothing plays from it when I try to play something. Any ideas?

Is there any more information you need from me?

Thanks for any help :)

---

### Post by blackhole82 on 2007-05-01
I have a similar problem with only my sound working in Audacity.  It worked fine everywhere else up until the other day.

---

### Post by sirlancelot on 2007-05-04
Ok funny story:

I decided to completely uninstall (read: purge) my sound drivers in an attempt to start with a "clean-slate" and then later reinstall them fresh. So I uninstalled alsa-base, alsa-utils, and linux-sound-base.

Here's where I get lost: I restarted my machine and to my (and probably of you) surprise, I HAVE SOUND! Why it works is beyond me and I certainly don't want to fuss around with it anymore, but I just thought I'd share that with anyone reading.

So if you want to try purging those 3 packages, go ahead. And if your case is not like mine, go ahead and reinstall them and see what happens :)

---

