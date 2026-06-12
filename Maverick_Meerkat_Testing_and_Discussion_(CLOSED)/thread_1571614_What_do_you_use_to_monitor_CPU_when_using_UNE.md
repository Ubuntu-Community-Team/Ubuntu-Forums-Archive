---
title: "What do you use to monitor CPU when using UNE?"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dsfitzpat on 2010-09-09
I'm currently trying out the beta version of Ubuntu Netbook 10.10, running the Unity interface, and previously ran UNE 10.04.
One of the little annoyances for me with the netbook interface is that the panel is locked, so you can't stick a panel system monitor applet anywhere.

In 10.04 I ran Docky at the bottom of the screen with a CPU monitor applet, using the intellihide feature to avoid taking up vertical space.  I'm thinking of doing the same in 10.10, but it doesn't seem to fit as well (aesthetically speaking) with the Unity interface.

Are other people using other solutions that work for them?  If so, what?
Of course, no monitor is an option, but I've only got a 3-cell battery, so if there's a runaway process I want to catch it ASAP!  (And while beta testing, you get your fair share of runaways...)

---

### Post by cariboo on 2010-09-09
This question would be better asked in the Maverick Testing & Discussion sub-forum. Moved.

---

### Post by uRock on 2010-09-09
Personally, I prefer running htop in a terminal and keeping it open.

---

### Post by cariboo on 2010-09-09
With an Atom 270 running Unity, it doesn't take long to find out if an app is running away.

---

### Post by dsfitzpat on 2010-09-10
Well I suppose on my eeePC the obvious tip-off is when the fan starts humming away at full speed!  But I also like being able to launch the system monitor with one click so I can identify and kill the running program.  Most of the panel and dock applets do this for you.

I've gone back to running Docky at the bottom of my screen since right now the unity interface doesn't have room for either a CPU monitor or a weather applet.  (I missing having the weather in my top panel.)
Any chance that we'll see some of the indicator-* packages (where *= weather, system, etc) in the repos at some point?

The other option I guess is to try something like desklets (similar to the kde plasmoid solution) but in the past I've found these didn't work nearly as well in gnome as they do in kde, so I used to just use the panel applets, before they were locked out.  I wonder if it would be possible to incorporate applets into the unity launcher?

---

### Post by dsfitzpat on 2010-09-11
Update regarding desklets: I installed gdesklets, but found that it does not run at all in a Unity session (I didn't check to see if this was a general problem in 10.10).  The screenlets program, on the other hand, seems to run reasonably well - although it doesn't get along perfectly well with Mutter (this is hard to say for sure: right now mutter crashes a lot, even without any screenlets running).

By the way, one (of many) usability/productivity features in Compiz that's not yet in Mutter is the widget layer.  If I'm running compiz in gnome and have screenlets set to widget mode, a simple keyboard shortcut toggles the screenlets between the background and foreground, whereas in Mutter I have to minimize any running applications to see (for example) the weather.

---

### Post by cariboo on 2010-09-11
Apparently the lone compiz developer is now/will be creating plugins for mutter instead, as it looks like compiz is dieing a slow death. Gnome 3 looks like it will use mutter instead of metacity for it's window manager.

---

### Post by MacUntu on 2010-09-11
I use htop via ssh on a second machine. :D

I miss my system monitor panel applet (CPU/RAM/NET) in Unity. :(

---

### Post by dsfitzpat on 2010-09-11
I've heard that compiz development was coming to an end... As an end user I was pretty happy with compiz - especially in the last couple of years - but if functionality in mutter can be brought up to a comparable level it probably won't make too much of a difference to the average user (eg: me) who isn't involved on the development side.
Of course I don't really care about losing plugins that are just for show (I'm pretty sure there's no practical use for drawing fire on the screen!) but I'd like to get back some of the keyboard shortcuts I used all the time - in particular, it would be nice if the 'super' key could find a use.
(Also, Alt+F2 doesn't work in Unity, which is unfortunate.)

For example, I like the workspaces button in Unity; since it displays both the workspaces and all the windows inside them I'd even say that it's better than the expo plugin in compiz, but if I'm doing keyboard work (eg document editing in LaTeX) it's much better to be able to hit Super-E than to have to go to my touchpad and then find the workspaces icon to click on it.  Aesthetically I preferred the Super-Tab flip switcher to the basic Alt-Tab switcher (and being able to point out to Vista users that in fact you didn't need advanced hardware to accomplish it) but I don't need it.

Will we see the sort of configurability in mutter that we had in compiz?  I can still use gconf-editor to give myself 4 workspaces, but I'd rather have them arranged in a 2x2 wall than in a 1x4 strip.  (I was a fan of the cube too, but that's not really essential.)

Anyway, the current interface is a good start, and now that it's out there I'm sure it will improve rapidly.  I'm hoping that some of the indicator applets now under development will be made available for the Unity panel at some point in the near future as well.

---

