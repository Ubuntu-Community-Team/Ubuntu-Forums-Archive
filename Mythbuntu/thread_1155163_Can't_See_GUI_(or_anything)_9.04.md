---
title: "Can't See GUI (or anything) 9.04"
date: 2009-05-10
forum: Mythbuntu
---

### Post by uncle hammy on 2009-05-10
I just installed 9.04 on my "testing" machine to give it a whirl before I even consider putting it on any of my "live" machines.

Right out of the gate, I have a show stopper, and I don't know how to overcome it.  When I boot up, the mythfrontend loads, the screen goes black and all I can see is the the drop shadow outline of a dialog box about the size of the "resizing theme" box, and that's it....just the outline.  If I press esc, I am greeted with the "are you sure" dialog....sort of.  What I actually get is a dark blue box with a light blue highlight bar at the top...No text, no images, nothing.  The highlight bar moves with the up and down arrows, and because I know option 2 is "Yes, Exit" I can exit.  Once I exit the frontend, everything is just fine.  At one point, I manged to blindly navigate my way to the settings screen, and it was a bunch of blue boxes where the textboxes would be, but no text or text on the buttons, etc.

I have hit enter at my blank outline, which should be "Watch TV", and it is.  Although, I get sound but no picture.

The machine is an AMD x64 5400+, 4 gigs memory, ATI x1300 video card.  I have also tried it with the onboard NVidia 6400.  I have tried using the i386 and 64bit versions.  Nothing seems to change it.

This was a clean installation over top of an 8.04 installation.  I gave the machine the same name, so that it would retain it's settings from the database (this has always worked for me in the past).  The only thing I can think of is perhaps a setting from the 8.04 installation is causing the problem with the new QT4 engine?  This machine was using the bluetoob wide theme, perhaps an issue with this theme and 9.04?

I have to be honest, I am so looking forward to Myth 0.22, but I am terrified that I won't be able to use it, because there hasn't been a usable release of Mythbuntu for me since 8.04.

---

### Post by uncle hammy on 2009-05-10
I can also tell you that I have installed 9.04 about 5 times today while trying to get this to work.  Each time, I select "Frontend Only" as my installation choice, and each time it sets it up as a secondary backend.

---

### Post by uncle hammy on 2009-05-10
OK another update.  I just did another installation, this tie giving it a completely new machine name to ensure I got completely fresh settings.  This had no effect, I still get empty "shells" (for lack of a better term) of the GUI.

I did get the "Can't find backend" screen, and it too was a big empty grey box, with a scroll bar, and a dotted line around what would be the top selection.  Nothing else.

I also made sure to install all updates, and all weekbuild updates.  No luck.

Really can't figure out what is going on here.

---

### Post by Neon Dusk on 2009-05-10
I think this is the bug reported [here](https://bugs.launchpad.net/ubuntu/jaunty/+source/mesa/+bug/341898).

---

### Post by uncle hammy on 2009-05-10
Thanks!  I was googling my little heart out and I don't know that  would have ever found that.

I am assuming that superm's patch is no longer in his ppa, because I added it to my repository and and ran all his updates and none of them fixed it.

However, adding Option "DRI" "off" worked.

---

### Post by nunrgguy on 2009-05-12
Not sure if I@ve got the same issue - did the upgrade on a front end, upgrade appeared to be installing all the backend gubbins too (not looked at it too much yet so don't know if it has..ahem).
Boots up fine and goes into mythtv...choose to watch live tv...ok, change channels etc...ok. 


BUT if you stop video  you arne't taken back to the menu, rather you just get the menu screen with surround but no actual menu or text within.

---

