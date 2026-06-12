---
title: "Setting Widescreen Resolution WITHOUT Using ATI Driver (on laptop)"
date: 2008-08-06
forum: Multimedia Software
---

### Post by Brerlapn on 2008-08-06
Issue:  My friend's laptop has an ATI card which has gone bad.  He is unable to run Windows on it at all.  I suggested Ubuntu, since I know you have to make a special effort to run proprietary drivers for video cards.  He installed 8.04 Hardy Heron just fine and has it running in 1280x1024 without any major glitches, unless he plays with the video settings too much--in which case the video goes haywire and he has to reset his xorg.conf file.  He is getting a Mac for work in a couple of months, so this solution only has to be good enough, not perfect.

Hoped-for Outcome: We are trying to set his laptop to run in either:

1) A widescreen mode (1600x1080; 1280x768 ) WITHOUT enabling the ATI card

 or

2) In 4:3 aspect with black bars on the sides of the monitor so that the graphics don't get squashed by displaying a 4:3 on a widescreen display (he would be happy to just set the display to horizontally squeeze the graphics and the aspect doesn't have to be mathematically exact).

I have played with the Screens and Graphics GUI and also tried editing the xorg.conf file to display at 1280x768, using various means I've run across on these forums, but so far to no avail.

Most threads on here regarding resolution are looking for ways to set up a display *using* the video card, which makes them unuseful for our purposes.  Our goals are modest--a reasonably widescreen resolution without invoking the broken ATI card, or some nice black bars on the left and right sides of the screen to maintain the image at 4:3, just like when you watch normal TV shows on a widescreen TV.

Anybody know how to do this?

---

### Post by Megatog615 on 2008-08-06
What ATI card is he using?

---

### Post by Brerlapn on 2008-08-06
> **Megatog615 said:**
> What ATI card is he using?

Honestly, I didn't ask, since we can't enable it.  All I know is that there is some sort of dreaded bug in the card that afflicts users at random, with catastrophic results for Windows (he can't even get through the setup on a freshly formatted hard drive in XP without the whole thing freezing up).  I can send an email to him and ask, though.

---

### Post by Megatog615 on 2008-08-06
You can easily find out on the command-line with the "lspci" command. If I knew which card it is maybe I could do some research on it...

---

### Post by Brerlapn on 2008-08-06
It's an ATI Mobility Radeon X600 with 256MB of RAM.  Thanks for your help.

---

### Post by Yellow Pasque on 2008-08-06
I don't understand what you mean by "reasonably widescreen resolution without invoking the broken ATI card"? How else are you going to display video? Perhaps you are using the vesa driver, which doesn't use video acceleration? I don't think VESA supports widescreen, but see if the resolution you want is available with:

```
xrandr -q
```

---

### Post by Brerlapn on 2008-08-09
Thanks for the help, folks.  Temujin's question led me to look up VESA drivers, widescreen resolutions, and video acceleration, and ran across the following thread:

[http://ubuntuforums.org/showthread.php?t=582246](http://ubuntuforums.org/showthread.php?t=582246)

Message #3 in that thread fixed the problem.  My friend reports that he is now running "faultless 1680x1050".

Thanks again for helping me walk through this and giving me some better focus on what I was looking for.

---

