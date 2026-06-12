---
title: "Amarok and Firefox-3.5 not sharing sound resources"
date: 2009-07-28
forum: Multimedia Software
---

### Post by bull8042 on 2009-07-28
I have found that since upgrading to Jaunty, and more recently Firefox-3.5 that I am have some playback issues. I am running a Dell E1505 with STA92xx.

If I am listening to Amarok and then start Firefox, I can continue to listen to music in Amarok but cannot listen to anything on the net. As long as I kill Amarok first, then start up Firefox, I can listen to youtube videos, no problem.

However, if Firefox is running first and I want to listen to Amarok, I have to shutdown Firefox and then manually kill nepomukserver BEFORE starting Amarok.

I know in the past, if I was listening to Amarok and started a video on youtube for instance, I could just pause Amarok. Otherwise both would play at the same time producing a muddled mess, but both would still play.

I understand having to stop one to listen to the other. But having to shutdown one completely before starting the other and even manipulating the nepomukserver manually can't be correct.

Is this a problem with my configuration, or is this a bug that the developers need to address?

---

### Post by argos3016 on 2009-07-28
It can be flash preferences. When you're in YouTube , for example , right click on video and settings, maybe you have the problem there or better, reinstall flash plugin.

---

### Post by bull8042 on 2009-07-28
> **argos3016 said:**
> It can be flash preferences. When you're in YouTube , for example , right click on video and settings, maybe you have the problem there or better, reinstall flash plugin.

No good. The preferences offered no help with regards to playback, only camera and microphone. As well, I already have the latest version.
Hmmm, thank anyway though.

---

### Post by igorzwx on 2009-07-28
It might be reasonable to have two Ubuntu 9.04 (in dual boot)
with different sound systems.
One of them may work.

Check if your hardware is supported by OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by Zorael on 2009-07-29
I'd wager that Flash is trying to output its sound via OSS while Amarok does it via ALSA (through Phonon). I'm not sure why it would, but perhaps it notices that you're not running PulseAudio - which is the default in Ubuntu nowadays - and as such freaks out and falls back to OSS?

---

### Post by igorzwx on 2009-07-29
your OSS is perhaps ALSA emulation of OSS.
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

many people have already changed to OSS4,
that is why, perhaps, your aps have OSS as default.

---

### Post by Zorael on 2009-07-29
But why would it use OSS in the first place? By *default* Flash should be set up to use ALSA, and as such you'd get sound mixing between it ando ther ALSA apps.

Obviously you could use a wrapper or tailor your entire sound system setup around what Flash is (probably) currently using, but the optimal solution would be to tell Flash to use whatever your other apps are using, which in the majority of cases equals ALSA. (or Pulse, if you want to think of it as something else than an API ontop of ALSA)

Does starting Firefox through the ALSA-OSS wrapper make it play nice with Amarok? You would need to install the **alsa-oss** package to try this.
```
$ aoss firefox-3.5 &
```
If it does, then Flash is indeed using OSS per default instead of ALSA. I'm not sure why nor how to tell it otherwise, though.

If you upgraded, do you have **libflashsupport** still installed from earlier versions?
```
$ apt-cache policy libflashsupport
```

---

### Post by igorzwx on 2009-07-29
I am not really a speciallist is such things.
From my personal experience, the most of apps use system default.
When, for example, you change to OSS4,
and change system default to OSS4,
the most of apps work out of the box (flash, Audacity, etc.).
Developers naturally prefer OSS to ALSA,
and, therefore, many things work well with OSS4.
There are some exotic apps (such as SoundJuicer, perhaps)
wich really need ALSA (there is a workaround to this problem)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
**Configure ALSA Apps to Use OSS (OPTIONAL)**

 In general, it's better to use applications that use the OSS API (or a higher level sound API/library) with OSS4, but if you choose to keep ALSA (instead of removing the alsa-base and alsa-utils packages), it's possible to have native ALSA applications output to OSS with [this workaround]("http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html").

---

