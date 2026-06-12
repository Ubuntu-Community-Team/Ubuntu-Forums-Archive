---
title: "Dual Monitors won't SLEEP in TwinView mode"
date: 2008-09-25
forum: Multimedia Software
---

### Post by BassKozz on 2008-09-25
I have a dual monitor setup, and [I recently switched]("http://ubuntuforums.org/showpost.php?p=5818944&postcount=6") from "Separate X-Sessions" to a "TwinView" and now my monitors won't go into standby mode. I've even changed the Power Management Preferences to put the display in sleep when inactive for only 2 minutes, and it still won't go into sleep after hours of waiting. When I was using "Separate X-Sessions" both monitors would go to sleep just fine...

Is there an issue with monitors going into sleep when using TwinView?

---

### Post by BassKozz on 2008-09-26
:bump:
 anyone?

---

### Post by BassKozz on 2008-09-27
Bug report filed: [https://bugs.launchpad.net/ubuntu/+bug/275308](https://bugs.launchpad.net/ubuntu/+bug/275308)

---

### Post by BassKozz on 2008-09-28
Also filed one at Bugzilla: [http://bugzilla.gnome.org/show_bug.cgi?id=554247](http://bugzilla.gnome.org/show_bug.cgi?id=554247)

---

### Post by BassKozz on 2008-09-29
Added to BrainStorm: [[IMG]http://brainstorm.ubuntu.com/idea/13875/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/13875/)

---

### Post by BassKozz on 2008-11-04
Still Broken in Intrepid (8.10) :(

---

### Post by BassKozz on 2009-05-04
Still Broken in Jaunty (9.04) :(...
Can someone PLEASE HELP ?

---

### Post by BassKozz on 2009-05-04
After some googling I found this page: [http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)
According to this page "vbetool" seems to be the solution.

Quick description of vbetool: "vbetool uses lrmi in order to run code from the video BIOS. Currently, it is able to alter DPMS states, save/restore video card state, and attempt to initialize the video card from scratch. It exists primarily in order to increase the chances of successfully recovering video state after an ACPI S3 suspend."
- [http://freshmeat.net/projects/vbetool/](http://freshmeat.net/projects/vbetool/)

So I tried what it said and used: sudo vbetool dpms off
And it Worked :-D !!!
Wait a minute not so fast...
I can't break out of it :-(
The monitors are stuck in standby mode... I tried moving the mouse, slamming my keyboard against my head, ctrl+alt+del... nothing seems to break it out of standby mode.  It seems that the GPU's BIOS is stuck in Standby Mode... I had to manually press the reset button on the box to get it to restart.

Hmm, off to do some more research.
Any idea's out there?

**Update:**
I think I might know why I can't get out of standby mode, or at least I have a guess.
When I try to run vbetool as user I get the following error messages:
```
open /dev/mem: Permission denied
Failed to initialise LRMI (Linux Real-Mode Interface).
```

So in order to initiate vbetool I need to use sudo.  So my assumption is that because I am running vbetool as sudo/root I can't get out of it by moving the mouse or keyboard because these are actions that are being performed as the user.
Maybe I am way off here, but it's just a guess.  Any idea's on how to run vbetool as user to test?

---

### Post by scarf on 2009-05-21
typing the following may bring your display back on:

```

sudo vbetool post

```

however, it would be nice if the display would just go to sleep automatically.

have you tried the beta nvidia 185 drivers?  i have, and my display still wouldn't sleep.  you can find those drivers here, [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

