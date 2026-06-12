---
title: "xrandr weirdness"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by kaplanmyrth on 2006-08-18
I have set up Dapper on a tablet, and I am having one or two niggling problems. The hardware is an HP TC1100, and I documented most of my efforts to get it running [on my blog, here]("http://andy.kaplan-myrth.ca/Main/20060814").

I actually have basically everything working -- the pen, the nvidia card (proprietary drivers!), suspend/resume... it's sweet.

Screen rotation also works -- at first, anyhow. My xorg.conf includes the line,
```
        Option          "RandRRotation"         "on"

```
I then run the following commands to rotate the screen:
```
xrandr -o left
xrandr -o normal
```

Now, that works perfectly for a while, but eventually (and I haven't been able to tell what the pattern is), it just doesn't rotate the screen anymore. I type the xrandr -o left command, and it responds:

```
$ sudo xrandr --verbose -o left
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 321mm x 241mm )  *60
 1    800 x 600    ( 321mm x 241mm )   60
 2    640 x 480    ( 321mm x 241mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right
Reflections possible - none
Setting size to 0, rotation to left
Setting reflection on neither axis

```

But it doesn't rotate the screen, it doesn't give an error message, and when I check the status, it says,

```
$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 321mm x 241mm )  *60
 1    800 x 600    ( 321mm x 241mm )   60
 2    640 x 480    ( 321mm x 241mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right
Reflections possible - none

```

Does anybody have thoughts on how I can troubleshoot this? What is stopping rotation from working?

---

### Post by Murgle on 2006-09-14
I get the same thing sometimes when I try to resize my screen.  It also works for a while and then vanishes.  I have also tried gnome-display-properties and it brings up the full dialog saying "do you want to keep this resolution?"  The most annoying thing is that it works for a while and then stops.  Ima poke about in logs and see if I can find anything that might say why this seems to happen.

---

