---
title: "Problems Installing TV Tuner"
date: 2009-02-20
forum: Multimedia Software
---

### Post by mkwilliams94 on 2009-02-20
I have just found and old TV tuner card and want to use it on my Ubuntu 8.10 machine. I installed the card but unlike Windows, Ubuntu does not identify any new hardware. After doing some reasearch with a friend I found that the card is old. I found a compatible driver for it at [http://linux.bytesex.org/v4l2/bttv.html](http://linux.bytesex.org/v4l2/bttv.html) but I do not know how to install the driver. Also, I am looking for software to watch my video on. Please help.

---

### Post by jovica lesevic on 2009-02-22
I have same problem with my Philips saa 7130 tv/fm card & Ubuntu 8.10.
TVtime television viewer dont respond on any kind of settings - result is black screen without sound.On my second boot system ( W XP ) tv/fm work with 
Honestech pvr without problems.
I need to fix this before remove WXP FROM COMPUTER FOR GOOD.

---

### Post by orethrius on 2009-02-22
> ** mkwilliams94]I have just found and old TV tuner card and want to use it on my Ubuntu 8.10 machine.[/quote]

Good first steps.  The key to a functional Linux system is a willingness to either use compatible hardware, or to experiment with other hardware.

[quote=mkwilliams94]I installed the card but unlike Windows, Ubuntu does not identify any new hardware.[/quote]

Betcha it *did*.  Try this and post (middle-click to paste, or just hand-type it in) your results (that little bar is right above the backslash '\', and it's critical that this be typed exactly as shown to get meaningful results).  Hold Alt and hit F2, then type the following said:**
> After doing some reasearch with a friend I found that the card is old. I found a compatible driver for it at [http://linux.bytesex.org/v4l2/bttv.html](http://linux.bytesex.org/v4l2/bttv.html) but I do not know how to install the driver.

It should literally be:
```
xterm -e 'tar xzvf bttv*.tar.gz; cd bttv*4; ./configure; make; gksudo make install;'
```

None of this is necessary, as both your (and jovica's) card is supposed to be supported by default.

[quote=mkwilliams94]Also, I am looking for software to watch my video on. Please help.[/quote]

xawtv is probably your best bet right off.  If you go to the Main Menu and click "Add / Remove...", once that loads, you can type **xawtv** in the Search line, tick the checkbox next to XawTV, and click "Apply Changes".  If you're looking for some way to watch video *files*, there are plenty of remedies for that as well.

[quote="jovica lesevic"]I have same problem with my Philips saa 7130 tv/fm card & Ubuntu 8.10.[/quote]

Did this work in 8.04 or earlier?  If so, there is either a configuration file that needs to be fixed, or the distribution regressed (read: hit a snag) somewhere along the line.

[quote="jovica lesevic"]I need to fix this before remove WXP FROM COMPUTER FOR GOOD.[/quote]

That's not an incentive around here.  Microsoft has done enough harm to justify their non-existance without additional merit.

---

