---
title: "Hardware 1080p acceleration in mplayer on HD4570"
date: 2010-12-12
forum: Multimedia Software
---

### Post by kaszak696 on 2010-12-12
Hello

I've tried watching material in 1080p resolution on my notebook and i experienced some slowdowns, tearing, etc. Video is encoded by x264 and sound is flac 5.1, all in mkv container. I know it's quite heavy one, but it was playing quite good on windows+CoreAVC, so i expect no less from my shiny Ubuntu :p I did a bit of googling and found out that AVIVO/UVD/Whatever is already turned on by default in fglrx drivers when using Xv, yet CPU is struggling on 90-100% load. Is there a way to turn hardware decoding on? It doesn't seem to work by "default" (or i'm too desperate to acknowledge that hardware acc is already on and still struggling to decode this :p).

Specs of my notebook:
Intel Pentium Dual-Core T4200 2.0 GHz
Mobility Radeon HD4570 256MB with fglrx from maverick repo
3GB RAM (doh!)
mplayer and codecs from medibuntu repo
mplayer uses -vo xv -va pulse , ffh264 and ffflac codecs

---

### Post by cchhrriiss121212 on 2010-12-12
First rule of graphics on Linux: ATI drivers are weak. You could try looking through the solution on this page, but it does not seem very user-friendly:
[http://ubuntuforums.org/showthread.php?t=1588465](http://ubuntuforums.org/showthread.php?t=1588465)

---

### Post by kaszak696 on 2010-12-12
> **cchhrriiss121212 said:**
> First rule of graphics on Linux: ATI drivers are weak. You could try looking through the solution on this page, but it does not seem very user-friendly:
[http://ubuntuforums.org/showthread.php?t=1588465](http://ubuntuforums.org/showthread.php?t=1588465)
Hmm, that topic gave me a hint about that vaapi thingy, thanks.
So my next question: Shall i compile mplayer-vaapi myself or are there any precompiled packages for maverick?

---

### Post by cchhrriiss121212 on 2010-12-12
I did find this:
[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/]("http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/")
It is a patch that you will need to apply to an already installed mplayer. If it works I'd be interested to know what kind of performance you get (ie cpu level reduction).

---

### Post by kaszak696 on 2010-12-12
So i compiled mplayer-vaapi from the latest source, and its quite promising so far. CPU stays at 40-50% at all times, so it looks like GPU finally did something. There are some problems tho: 

[LIST=1]
[*]i had to install quite outdated libva-0.31.1 from [http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/") . I'm still looking into it, perhaps i'll manage to patch 1.0.1 from maverick repo to make it work work too.
[*]You cannot move mplayer window on the desktop unless you want some nasty artifacts to show off. Fullscreen works fine (but doesn't clear glitches if they already happened). EDIT It appears that Compiz causes these glitches
[/LIST]
Only 2 issues, tbh i expected a lot more ;). I'm going to poke the issue a bit further.

---

