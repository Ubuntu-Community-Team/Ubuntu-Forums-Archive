---
title: "Screensaver in 9.10"
date: 2009-11-24
forum: Mythbuntu
---

### Post by zapstrap on 2009-11-24
Just upgraded from a mythbuntu 9.04 installation to ubuntu 9.10.  It looks like mythtv got upgraded to 0.22 in the process.

The old xscreensaver vanished, and in its place was gnome-screensaver.  This screensaver simply does not work, and I'd rather not make a project out of discovering why.  I uninstalled it and put back xscreensaver, thinking I'd go with what worked.

xscreensaver works, but now I have a new problem.  In 9.04, the screensaver would come on when mythtv was running if you left it alone on any of the menus (i.e. not watching a programme).  If you were watching a programme, the screensaver would not come on.  The same applied to watching a programme using vlc.  Now the screensaver comes on if watching a programme.

So it appears I've traded one project for another.  Instead of trying to figure out why gnome-screensaver doesn't work, I now need to find out why xscreensaver doesn't step aside when video content is on the display.  Can anybody suggest where I might look to sort this out?

---

### Post by superm1 on 2009-11-24
There's two problems actually:

1)
So what happened is gnome-screensaver switched to using the gnome-session interface.  We didn't realize until late in the 9.10 cycle that this happened, and it was too late to sort out adding xscreensaver in it's place as a better solution.

2)
In switching to the gnome-session interface, upstream broke gnome-screensaver's --poke functionality for turning off the screensaver.  This means that in standard Ubuntu installs with gnome, no apps are able to disable the screensaver using that --poke command.

---

### Post by williammanda on 2009-11-24
> **superm1 said:**
> There's two problems actually:

1)
So what happened is gnome-screensaver switched to using the gnome-session interface.  We didn't realize until late in the 9.10 cycle that this happened, and it was too late to sort out adding xscreensaver in it's place as a better solution.

2)
In switching to the gnome-session interface, upstream broke gnome-screensaver's --poke functionality for turning off the screensaver.  This means that in standard Ubuntu installs with gnome, no apps are able to disable the screensaver using that --poke command.

Is there a fix in the works?

---

### Post by superm1 on 2009-11-24
For problem #2 there is a fix in the works by Ubuntu developers, but no recent updates:

[https://bugs.edge.launchpad.net/ubuntu/+source/vlc/+bug/428884](https://bugs.edge.launchpad.net/ubuntu/+source/vlc/+bug/428884)

Problem #1 won't be fixed for 9.10

---

### Post by zapstrap on 2009-11-24
So, is there a work-around with xscreensaver?  I notice most of the discussion on the ubuntu developers page is centred around vlc not interoperating with gnome-screensaver.  xscreensaver used to not come on when video content was playing, and I uninstalled the gnome screensaver.  Is there some sort of work-around involving a little script?  I know this isn't the place to make a wish, but I'll do it anyway:

Why can't the screen saver have a config file in the user's home directory with a list of apps to interlock with?  In a perfect world, it'd be smart enough to only lock-out when video content is playing, or when playing music with a visualizer enabled.  I'm not sure if this is a stupid question, so please don't charbroil me.

---

### Post by kja999 on 2009-11-24
> **zapstrap said:**
> So, is there a work-around with xscreensaver?  I notice most of the discussion on the ubuntu developers page is centred around vlc not interoperating with gnome-screensaver.  xscreensaver used to not come on when video content was playing, and I uninstalled the gnome screensaver.  Is there some sort of work-around involving a little script?  I know this isn't the place to make a wish, but I'll do it anyway:

Why can't the screen saver have a config file in the user's home directory with a list of apps to interlock with?  In a perfect world, it'd be smart enough to only lock-out when video content is playing, or when playing music with a visualizer enabled.  I'm not sure if this is a stupid question, so please don't charbroil me.


use xset at a command line to see the options available .. find what you need and add that to rc.local

ie tun off power save. ```
xset -dpms
```

---

### Post by ZedThou on 2009-11-24
Followup to  kja999: for me this was fixed by putting the following in ~/.xprofile

```

xset -dpms
xset s off

```

---

### Post by zapstrap on 2009-11-24
I should point out that disabling the screensaver using its own controls works fine.  I just thought it'd be nice to not leave a fixed menu up on that burn-in prone plasma display. :)

---

