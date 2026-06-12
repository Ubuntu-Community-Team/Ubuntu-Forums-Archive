---
title: "[SOLVED] 2 Screens"
date: 2008-08-18
forum: Multimedia Software
---

### Post by finito on 2008-08-18
I have a 42" LCD HDTV and a 19" LCD Display,
I have connected both screens one via DVI the other through HDMI.

When I use 2 screens in Clone mode the computer gets seriously slow
(Intel Q9450 Quad Core, 4GB RAM, 9600 GT, WD 150GB Raptor Drive)
I don't understand why. 

I have 2 desktops enabled, what I want to do is basically make it so if I drag the window off the screen it should appear on the TV or if possible, when I watch a video for it to appear on the TV.

is this possible?

I don't know if this should be in Hardware or Multimedia.

---

### Post by draclear on 2008-08-18
If you're using an nvidia card try the following, which works for me.

Make sure you have nvidia-settings installed:

[INDENT]sudo apt-get install nvidia-settings[/INDENT]

From a terminal run the programme in sudo mode:

[INDENT]gksu nvidia-settings[/INDENT]

Ask it to detect monitors and then choose your settings as appropriate.  It won't be able to apply them right away so make sure you save to the X-config file (there's a button for this) and then restart X, either by rebooting or:

[INDENT]CTRL-ALT-F1
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start[/INDENT]

Substitute gdm with kdm is you're using kde as your default desktop manager.  Should do it.  You'll probably need to fiddle about with the settings a bit, but if you're using Linux that's probably not going to be too difficult.

---

### Post by finito on 2008-08-18
that is how I got it to go into dual screen Clone mode. But what happens is that I get 2 Desktops on the LCD Monitor, and one separate one on the TV, I can't click on it or anything.

---

### Post by finito on 2008-08-19
[http://ubuntuforums.org/showthread.php?t=240150](http://ubuntuforums.org/showthread.php?t=240150)

---

