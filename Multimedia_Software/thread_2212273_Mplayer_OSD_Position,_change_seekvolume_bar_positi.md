---
title: "Mplayer OSD Position, change seek/volume bar position."
date: 2014-03-20
forum: Multimedia Software
---

### Post by Dr_Frost on 2014-03-20
I the 5+ years i been running linux i have never found a way to do as title suggests...

I pretty much only use mplayer as i just works and is the most customizable player i know of, but one config/setting i have NEVER gotten to word/found is how to change the seek/volume bar so it is in the top or bottom of the screen, i have always felt it is very ignoring to have it in the CENTER of the video.

Can this even be done or is it just one of the things that is hard coded into mplayer and in all the 1000' of things you can change to your liking, you just can't change this....

---

### Post by matt_symes on 2014-03-20
Hi

Have you tried ..

```
# OSD progress bar vertical alignment 
progbar-align=50
```

from here 

[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)

Kind regards

---

### Post by Dr_Frost on 2014-03-20
No haven't tried that, but still no change no matter the value i set it at :(, considering the hours i spent searching forums and pretty much every mplayer config setting etc... still no dice after all this time, still think it is weird considering all the things you can change, you just can't change this....

---

### Post by matt_symes on 2014-03-20
Hi

Just tried it myself and no luck either. 

Even  the **&#8722;progbar&#8722;align **parameter does not work for me either :(

I may be no help here. Sorry.

Kind regards

---

### Post by mc4man on 2014-03-20
You should add this to a new line in  ~/.mplayer/config, ie. this will move to bottom
```
progbar-align=100
```

---

### Post by Dr_Frost on 2014-03-20
> **mc4man said:**
> You should add this to a new line in  ~/.mplayer/config, ie. this will move to bottom
```
progbar-align=100
```

That function unfortunately does nothing, no matter what placement in config or what value

---

### Post by mc4man on 2014-03-20
> **Dr_Frost said:**
> That function unfortunately does nothing, no matter what placement in config or what value

Then maybe your mplayer build is too old, works fine here

---

### Post by Dr_Frost on 2014-03-22
> **mc4man said:**
> Then maybe your mplayer build is too old, works fine here

You may be right... 

```

MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
Warning unknown option progbar-align at line 1

```

How do i get the latest version, i have tried this but with no luck so far.....
Ubuntu 12.04 - Mate Desktop

---

### Post by mc4man on 2014-03-22
You could - 
search this forum for  instructions on how to build mplayer2 (development stopped) or mplayer
search for a mplayer2 ppa for 12.04

If you want a recent mplayer via a ppa for precise then I have here, please note that mencoder is Not included nor do I have any intent to add it
(the ppa 12.04 mplayer requires libopus which is in ppa for 12.04
[https://launchpad.net/~mc3man/+archive/mplayer-test](https://launchpad.net/~mc3man/+archive/mplayer-test)

---

### Post by Dr_Frost on 2014-03-22
Awesome now that works :) and everything else seems to work, but one thing that is buggy and why i went with mplayer2 is that i use left/right button + scroll to seek, and if i scroll to fast i "cut's out" and i have to let go and press down left/right and scroll again abit slower to seek more...., this gets ignoring so is there a fix or a setting that limits scroll speed?

```

MOUSE_BTN0-MOUSE_BTN3 seek +7
MOUSE_BTN0-MOUSE_BTN3_DBL seek +7
MOUSE_BTN0-MOUSE_BTN3-MOUSE_BTN3_DBL seek +7
MOUSE_BTN0-MOUSE_BTN4 seek -7
MOUSE_BTN0-MOUSE_BTN4_DBL seek -7
MOUSE_BTN0-MOUSE_BTN4-MOUSE_BTN4_DBL seek -7

MOUSE_BTN2-MOUSE_BTN3 seek +60
MOUSE_BTN2-MOUSE_BTN3_DBL seek +60
MOUSE_BTN2-MOUSE_BTN3-MOUSE_BTN3_DBL seek +60
MOUSE_BTN2-MOUSE_BTN4 seek -60
MOUSE_BTN2-MOUSE_BTN4_DBL seek -60
MOUSE_BTN2-MOUSE_BTN4-MOUSE_BTN4_DBL seek -60

```

---

### Post by Dr_Frost on 2014-03-23
[**[COLOR=#000000]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715")  do you have an idea/fix for the to fast scrolling bug?, after testing  alot of video format's and such everything else just works with your  MPlayer :), just need that small little fix.

---

### Post by mc4man on 2014-03-23
> **Dr_Frost said:**
> [**[COLOR=#000000]mc4man[/COLOR]**]("http://ubuntuforums.org/member.php?u=320715")  do you have an idea/fix for the to fast scrolling bug?, after testing  alot of video format's and such everything else just works with your  MPlayer :), just need that small little fix.
Honestly don't get what your issue is & here generally use mpv now for local files.

You could consider posting to the mplayer users mailing list 
[http://lists.mplayerhq.hu/mailman/listinfo/mplayer-users](http://lists.mplayerhq.hu/mailman/listinfo/mplayer-users)

---

### Post by matt_symes on 2014-03-25
Hi

Thanks mc4man. Just update my mplayer using your PPA.

Old... 

```
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
```

New...

```
MPlayer SVN-r36810 (C) 2000-2012 MPlayer Team
```

The repos don't have cutting edge builds. Must fix my arch install.

Memcoder - shemcoder :D

Kind regards

---

### Post by andrew.46 on 2014-03-25
> **matt_symes said:**
> ```
MPlayer SVN-**[COLOR="#FF0000"]r36810[/COLOR]** (C) 2000-2012 MPlayer Team
```

It is easy to fall behind, even with mc4man's great PPA, latest:

```

andrew@ilium~$**[COLOR="#FF0000"] svn info svn://svn.mplayerhq.hu/mplayer/trunk[/COLOR]**
Path: trunk
URL: svn://svn.mplayerhq.hu/mplayer/trunk
Repository Root: svn://svn.mplayerhq.hu/mplayer
Repository UUID: b3059339-0415-0410-9bf9-f77b7e298cf2
**[COLOR="#FF0000"]Revision: 37069[/COLOR]**
Node Kind: directory
Last Changed Author: ib
Last Changed Rev: 37069
Last Changed Date: 2014-03-26 00:45:52 +1100 (Wed, 26 Mar 2014)

```

---

