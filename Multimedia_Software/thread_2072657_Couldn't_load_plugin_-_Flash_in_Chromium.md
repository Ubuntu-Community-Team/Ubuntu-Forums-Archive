---
title: "Couldn't load plugin - Flash in Chromium"
date: 2012-10-18
forum: Multimedia Software
---

### Post by komarx6 on 2012-10-18
I tried to find solution but I just couldn't. Does anyone of you know how to fix this problem?
When I try to watch videos on YouTube, Chromium says "couldn't load plugin".
There was flashplugin-installer already installed , but I reinstalled it, and Chromium(it did't help). I also tied to copy libflashplayer.so to /etc/lib/chromium-browser/plugins.

```
chromium-browser --enable-plugins
``` does not help neither, and flash plugin is already enabled.

Please help.
Thank you.

---

### Post by kc1di on 2012-10-18
have you installed ubuntu-restricted-addons and ubuntu-restricted-extras yet?

in not do that first.
Then see if it works.

---

### Post by komarx6 on 2012-10-18
It was installed already.
It seems that this happens only with some videos, while I can watch others, both on same site - YouTube. It's strange, really.
I tried playing one .flv and one .mp4 file that were downloaded on another computer for youtube months ago. But it couldn't play. I can play .mp3 files and hear audio of above mentioned files in audacious and vlc but not in default mplayer.
I installed Lubuntu recently, and never tried to play any multimedia files before.
What's happening? How can I play this videos in Lubuntu.

---

### Post by kc1di on 2012-10-18
I'm not sure what is wrong then, I have Lubuntu loaded on this machine with lubuntu-restricted-extras and lubuntu-restricted-addons and everything work wonderfully. mp3 mp4 flash all working.

you can try uninstalling those files and reinstalling them that might work for you.

---

### Post by komarx6 on 2012-10-20
I found out what was the problem. My machine is simply too old. I had to install older version of Flash downloaded from Adobe's site.
I am sorry for bothering you.

---

### Post by posfan12 on 2012-12-04
I am having the same issues. The plugin is installed/enabled but the "Couldn't load plug-in" message appears instead of the Flash video/ad/whatever. How did you determine your computer was simply "too old" (my computer is fairly old as well), and from where did you obtain the older Flash plugin?

[edit]
I found the problem and solution are explained here:

[http://forums.debian.net/viewtopic.php?f=10&t=82710](http://forums.debian.net/viewtopic.php?f=10&t=82710)

Recent versions of Flash require a CPU that supports SSE2 instructions. Otherwise you have to revert to an older version of Flash, which is what I had to do.

---

