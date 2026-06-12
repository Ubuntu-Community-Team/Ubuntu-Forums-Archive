---
title: "[SOLVED] Simultaneous sound in different applications"
date: 2008-07-18
forum: Multimedia Software
---

### Post by alberto ferreira on 2008-07-18
Hi, I wish to have sound in Ubuntu 8.04 in several applications at the same time.

For instance:
If I'm playing music with Rhythmbox I need to close it every time I want to watch a video in Firefox 3,say, on youtube. If I don't, I don't get any sound at all from Firefox 3. (And vice-versa)

I have the latest patches and I've installed "libflashsupport" to solve this problem but I had to remove it because Firefox became so unstable that I could no longer use it.

Libflashsupport is buggy,so, is there another way I can have sound simultaneously in different applications without having to close them / making firefox unstable?

Thanks

---

### Post by mefistofeles666 on 2008-07-18
I read you can have vlc and firefox share audio without having to close either, just set vlc audiooutput to pulseaudio and listen to your music there.

I tried it but I couldn't listen to any music in any other application, and never had simultaneous audio either but u can try it and see if it works.

 Installing VLC Media Player

At the console, type:

  sudo apt-get install vlc

To remove,

sudo apt-get --purge autoremove vlc

If you encounter sound problems (due to PulseAudio ), type:

   sudo apt-get install vlc-plugin-pulse

and choose PulseAudio as output in VLC options. 


if you do find a solution dont forget to share :P

---

### Post by xc3RnbFO8P on 2008-07-18
Read this:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by Mister.Vash on 2008-07-18
Take a look at this thread
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

You could also try the new beta version of flash, it has pulseaudio support which may fix the issue
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

