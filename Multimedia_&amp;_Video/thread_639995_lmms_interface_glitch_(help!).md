---
title: "lmms interface glitch (help!)"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by linuxmann on 2007-12-13
I installed lmms fine. When i ran lmms it seems to have a serious GUI glitch. The buttons do not have text on them. The background changes to different colors each time i run lmms. The glitch is to the point where the sound does not work and i cannot use the program itself. Can somebody help me with this problem? Here is what it looks like.

[IMG]http://img262.imageshack.us/img262/8350/screenshotea1.png[/IMG]

---

### Post by BCtom on 2007-12-14
Hi Linuxmann,

I couldn't help notice first that the version (0.2.1=Sept 2006 build) you have of LMMS is very old. If you downloaded with Synaptic, you should of at least gotten version LMMS-0.3.0. I have a hunch that this may be your problem. I know it relies on Qt 3.x for its GUI, that could be a problem using an older version.

Also for sound, you need ALSA-lib, JACK or SDL for your sound card. 

 Go to [LMMS]("http://lmms.sourceforge.net/") download page and see what you need, then install everything with Synaptic. I was up and running with in fifteen minutes.

---

