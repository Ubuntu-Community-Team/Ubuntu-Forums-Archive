---
title: "Turn off screen blanking and power off?"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by jakev383 on 2007-05-15
I have a MythTV setup that is working great.
The only problem I have is now that the machine is all setup and wired into my Tv and entertainment center, I find that after 10-15 minutes of idle it shuts off the video output. Like it's trying to put the monitor to sleep. Too bad it's a TV! 
Does anyone know of a way to stop this from the CLI? 
I've already tried:
Commenting out Option "DPMS" in xorg.conf
gconftool-2  --set "/apps/gnome-screensaver/idle_activation_enabled" --type boolean false
killall gnome-screensaver

And I (foolishly) tried apt-get remove gnome-screensaver. Which also removes Gnome and kills the frontend portion of MythTV for those that aren't brave enough to try themselves.
Any help is appreciated!

---

### Post by earobinson on 2007-05-15
have you tried turning of the screensaver using the gui?

---

### Post by jakev383 on 2007-05-15
> **earobinson said:**
> have you tried turning of the screensaver using the gui?

I was hoping on a way to do it from remote (no keyboard or mouse, remote control via LIRC). I'll try doing it the other way later today.

---

### Post by jakev383 on 2007-05-15
Okay, tried that. Didn't know what to do. When I login all I get is a blank screen (tan colored), and when I right click the mouse I get a toolbar that is titled "OpenBox" for the WM being used. I'm totally lost after that :? 
Thanks for the suggestion though!

---

