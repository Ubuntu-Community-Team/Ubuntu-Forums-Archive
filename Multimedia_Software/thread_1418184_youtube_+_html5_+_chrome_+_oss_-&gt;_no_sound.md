---
title: "youtube + html5 + chrome + oss -&gt; no sound"
date: 2010-02-28
forum: Multimedia Software
---

### Post by monkman on 2010-02-28
anyone has a solution for that? i'm using a maudio revolution 5.1 soundcard, so that i have to use the opensound driver. on my notebook it runs fine with the standard alsa driver.

using 9.10 64bit.

thx!

---

### Post by Yellow Pasque on 2010-02-28
Unfortunately, no good solution at the moment: [http://code.google.com/p/chromium/issues/detail?id=19470](http://code.google.com/p/chromium/issues/detail?id=19470)

Using ALSA emulation with libasound2-plugins ( [http://www.opensound.com/wiki/index.php/Tips_And_Tricks#ALSA_Emulation](http://www.opensound.com/wiki/index.php/Tips_And_Tricks#ALSA_Emulation) ) gives sound, but it doesn't sync well with the video.

---

