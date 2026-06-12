---
title: "Unable to use Gutsy Live CD, stuck in low resolution mode"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by ilektron on 2008-01-22
Okay, so after getting frustrated with ubuntu, trying PCLinuxOS, Mint, Sabayon, nothing works out of the box for one thing or another...

So I'm back to trying to get Ubuntu to work

The Live CD switches to low resolution mode.  No matter what I do I can't change the Screen and Graphics settings.  Another thing that makes it difficult is that the font size is so small it makes it unreadable.

Everything worked in feisty, it took some tweaking, but I never had this problem

Here's some data:
ATI AIW 9600
lspci output:
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

I have the computer hooked up to a Vizio 37" LCD (vx37l)
Ah, Ok, I'm getting "No valid modes" in /var/log/Xorg.0.log.old

Tried the modeline info here:
[http://www.mythtv.org/wiki/index.php/Vizio_VX37L](http://www.mythtv.org/wiki/index.php/Vizio_VX37L)

Same problem.  Curse you low res mode!

So I assume I need a modeline that works, but none that I've found work.  Anybody got any ideas?

---

