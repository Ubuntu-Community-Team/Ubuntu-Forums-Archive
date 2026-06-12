---
title: "Flash videos crash desktop but not music"
date: 2011-11-01
forum: Multimedia Software
---

### Post by Matyy on 2011-11-01
Hey,

I find a lot of topics about flash crashing something, but I couldn't find any fix yet.

Flash videos sometimes crash my desktop. First flash loads, only after trying to start the video it crashes. Sometimes &#8211; not regularly, but rather often. It doesn't matter if it's youtube, dailymotion or just a random video. Non-video flash doesn't seem to crash.

The crash: Everything freezes. Cannot move the mouse, cannot use the keyboard, screen is frozen. I can't even switch to the terminal. But music, if some is playing continues.

[LIST]
[*]I searched whether there is more than one flash installed (with locate) &#8211; didn't find any.
[*]It happens in firefox with flash from the repositories as well as in chromium with it&#8217;s own flash.
[*]I have a nVidia video card and the drivers nvidia-current from the repos.
[*]It doesn't matter whether I am using metacity or compiz or kwin.
[*]I&#8217;m using twinview, but it happens without twinview, too.
[*]System is 32bit.
[*]If I open the settings (right click - settings), I cannot click the settings, but I heard that&#8217;s rather common.
[/LIST]
Thanks

---

### Post by inobe on 2011-11-01
using kubuntu 11.10 atm, when i had 11.04, it seemed that it started to crash on me after i installed chrome.

in 11.10 now, i refuse to install chrome.

just a shot in the dark, i am not certain chrome caused my crashes, and not willing to find out again!

---

### Post by Matyy on 2011-11-02
Well I already deleted chrome's flash manually. I tried the extension flash-aid and let it install the flash beta version. After that it froze a bit differently, sometimes I could move my mouse a bit. But well, after a few minutes without real response, without being able to switch to the terminal, I still had to shut my PC down.

Now I try it without the hardware acceleration option.

---

### Post by Matyy on 2011-11-06
Turning off hardware acceleration didn’t work.

---

### Post by beew on 2011-11-06
Which version of Ubuntu do you use? It seems to be a Nvidia problem.
[http://www.nvnews.net/vbulletin/showthread.php?t=161664&page=8](http://www.nvnews.net/vbulletin/showthread.php?t=161664&page=8)

Try update your driver with the xswt ppa

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Rick B. on 2011-11-09
I've had the same problem in 10.10, 11.04 and Mint 11 with Firefox on a Dell Dimension 8400 desktop. I have a Sound Blaster Audigy 2 ZS sound card with CA0106 chipset. Any suggestions for solving this problem as it is driving me crazy. Thanks.

---

### Post by MoreOrLess on 2011-11-09
If it was just Flash crashing, it shouldn't take out the whole system. It sounds like overheating to me. Flash video is known to stress the CPU and cause overheating on improperly cooled systems (especially laptops that need dusted out or don't have the correct ACPI fan control in Linux.)
Monitor your CPU temps.

---

### Post by Matyy on 2011-11-14
Hm, I am trying the drivers. I don’t think it’s overheating, I am monitoring anyway, but the music shouldn’t continue playing, if it’s overheated, should it? I think it should be something about the video card, tough, since it seems, as if my computer keeps running while it’s visual representation freezes so hard, I can’t even change to a terminal.

---

### Post by Matyy on 2011-11-16
So, with the new graphic drivers + flash beta it doesn’t seem to freeze any more. But flash crashes very often – only videos tough. So I tried new drivers + repository flash &#8594; it freezes the whole system again. So I will stay with beta for now, since than at least only the videos crash.

---

### Post by Matyy on 2012-01-27
It freezes again and again, I can't get rid of this problem. Still no ideas?

---

