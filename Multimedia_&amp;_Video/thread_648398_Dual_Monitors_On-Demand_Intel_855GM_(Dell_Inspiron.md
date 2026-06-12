---
title: "Dual Monitors On-Demand Intel 855GM (Dell Inspiron 700m)"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by flamacue on 2007-12-23
Nevermind, I don't think this is going to work the way it does in Windows, let alone with the extra flexibility often afforded by Linux.  :(  (I have also tried following this guide
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)
to a tee--no love.)

I think a lot of things need work here, including the "intel" driver (for the 800/900 series graphics), xserver, and naturally tying into the GUI.

Any devs listening?  Is there work on this stuff for Hardy?

The monitor configurator GUI (sorry I forget the name) is great for a static desktop display.  But since it lacks hotplug support, it's much less than ideal for my laptop use, as I'd need to be able to enable/disable the VGA on the fly.



======== Original Message + 1 edit ==============

Just upgraded to Gutsy, the monitor config is nice, but not good enough for my purposes.  I have a Dell 700m (Intel 855GM graphics using "intel" driver), and I want to be able to enable/disable the VGA output, with a different resolution from my built-in LCD ("LVDS"), as a desktop extension, *on-demand*.  And I want the default to be VGA OFF.  The tool of choice is xrandr.

I'm close.  I've been through so many iterations, I apologize, I can't really say exactly how I got to this point.  At the moment, at the GNOME login window, it mirrors the output on LVDS to the VGA out, but my scripts work.  If I could just get it to turn off that output but still let my scripts work, I could live that.

My xorg.conf is attached.

My disable script runs:

xrandr --output VGA --off

and my enable script runs:

xrandr --output LVDS --auto --output VGA --mode 1280x1024 --above LVDS


Man am I looking forward to real hotplug support!  (Is it coming in Hardy?)


EDIT:  It seems the presence of the VGA is autodetected at the login screen (i.e. at X startup?).
[LIST]
[*]If the monitor is connected, the output will mirror the 1200x800 output to the VGA, and my scripts will work.
[*]If the monitor is not connected, it will not display on the VGA when I do connect it, but my scripts will not work!
[/LIST]

---

### Post by Craigus on 2007-12-23
Does this help:

[http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html]("http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html")

---

### Post by flamacue on 2007-12-23
> **Craigus said:**
> Does this help:

[http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html]("http://budlite.blogspot.com/2007/09/hotplugging-secondary-display-on-linux.html")

That guy is talking about using Xorg 7.3.  I don't think that's been fully integrated into Ubuntu yet...

[http://digg.com/linux_unix/Xorg_7_3_delayed_until_Ubuntu_s_April_release_Bullet_proof_X_postponed](http://digg.com/linux_unix/Xorg_7_3_delayed_until_Ubuntu_s_April_release_Bullet_proof_X_postponed)

...though I was hoping that the pieces included so far would let me do what I described above.  (Seems not.)

---

### Post by Craigus on 2007-12-23
Hmm. I had thought it was xrandr 1.2 that provided this functionality, which we do have, but perhaps you are right.

---

### Post by alperyilmaz on 2008-05-23
Hi flamacue,

Did you find a better solution for the problem? I also have Inspiron 700m and I'm suffering from bad experiences with dual monitors.

thanks..

---

