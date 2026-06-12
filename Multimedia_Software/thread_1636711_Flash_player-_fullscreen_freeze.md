---
title: "Flash player- fullscreen freeze"
date: 2010-12-03
forum: Multimedia Software
---

### Post by pp_1 on 2010-12-03
Hi, I'm new here and I hope I've put this thread in a correct section.

I had a problem with flash player on my Ubuntu 10.10 x64. When I was switching video (YouTube for example) into fullscreen I was able to hear the sound, but video was frozen.
I've been searching for the solution for a very long time, but the only thing I've found was adding OverrideGPUValidation=true to mms.cfg. Unfortunatelly, it doesn't work on x64.

I've tried flashplayer reinstallation, upgrading to betas and few others. Nothing worked.

The solution's very simple.
1) Go to [www.youtube.com]("http://www.youtube.com") and start playing any movie.
2) RMB on player -> settings
3) Hardware acceleration ON
4) Third icon-> let s.ytimg.com save data on your computer with no limit
5) Everything's working great! :p

The amount of data that flash player can store on your computer is 2kB (!) by default...

--------
Ubuntuforums.org admins: I know I've made a lot of mistakes, 'cause my english's not good- correct it, please...

---

### Post by madjr on 2011-02-07
thx for the tip, and for 32bit a few solutions here:

[http://ubuntuforums.org/showthread.php?t=1068680](http://ubuntuforums.org/showthread.php?t=1068680)

---

