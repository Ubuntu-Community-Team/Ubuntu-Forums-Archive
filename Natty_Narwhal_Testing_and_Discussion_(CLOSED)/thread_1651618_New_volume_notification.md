---
title: "New volume notification"
date: 2010-12-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by anders_c_ on 2010-12-23
Did some updates and this new volume notification showed up.

Not really sure if I like this one...it takes up so much space!

---

### Post by cariboo on 2010-12-23
It looks like you've got something broken, as that is the old gnome volume indicator.

---

### Post by jmmL on 2010-12-23
> **cariboo907 said:**
> It looks like you've got something broken, as that is the old gnome volume indicator.

I'm seeing this as well, and I'm just keeping up-to-date with the main natty repos and nothing else.

---

### Post by efflandt on 2010-12-23
I only get the good icons once in a great while.  Anytime I have to do unity --reset or compiz --replace to get unresponsive panel applets and other menus to respond, I end up with these plain default icons.  I actually had the same problem in Karmic when playing around with themes (and never could figure out how to fix that).  But I have not changed any appearance since I reinstalled one of the dailies last weekend and some updates since then.

How do you get the good icons back?

PS: 1st image is bad icons and I don't know what I did to get good icons (for the moment) in second image (restarting gdm a bunch of times when menus were not working right after unity --reset or compiz --replace).  But I imagine they will only be there this session.

---

### Post by zekopeko on 2010-12-24
> **efflandt said:**
> I only get the good icons once in a great while.  Anytime I have to do unity --reset or compiz --replace to get unresponsive panel applets and other menus to respond, I end up with these plain default icons.  I actually had the same problem in Karmic when playing around with themes (and never could figure out how to fix that).  But I have not changed any appearance since I reinstalled one of the dailies last weekend and some updates since then.

How do you get the good icons back?

PS: 1st image is bad icons and I don't know what I did to get good icons (for the moment) in second image (restarting gdm a bunch of times when menus were not working right after unity --reset or compiz --replace).  But I imagine they will only be there this session.

I also saw this happen. For some reason the gnome-settings-daemon isn't starting up.

---

### Post by mc4man on 2010-12-24
While this is just an opinion - I'd refrain from using unity --reset or compiz --replace if at all possible - there should be no need.
If booting to unresponsive icons, menu items, ect. then try exposing a r. click context menu and or open a dir. on the desktop. If those don't work or you boot to a spinning cursor or other mis behavior that a restart of x should fix (enabling Ctrl+Alt+backspace is an easy way.

If Desktop > unity continues to not load cleanly then maybe try Classic > unity (enable the unity plugin in ccsm, remove bottom panel and don't reload any applets if prompted on a restart.
(or do a fresh install

---

### Post by efflandt on 2010-12-24
I misunderstood the OP and thought a blow up of the applet icon was inserted for easier viewing (like I did), rather than what popped up when clicking sound applet.  I rarely even get normal icons with my system constantly reverting to plain icons with dirty gray drop down boxes for applets (once I wake them up) probably due to .xsession-errors:

```
** (gnome-settings-daemon:1413): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1413): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
No value set for `/apps/compiz-1/general/allscreens/options/active_plugins'
``````
I/O warning : failed to load external entity "/home/efflandt/.compiz/session/104fe738be18c2abeb129321715779357300000013590027"
Initializing session options...done

(nautilus:1437): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Initializing unityshell options...done
```And a flood of GLib-GObject errors like "invalid cast from `BamfWindow' to `BamfApplication'" for something unknown, and "invalid uninstantiatable type `(null)' in cast to `GObject'" for gedit.

At least I learned how to wake up the applets and menus by right clicking the desktop (opening and closing file manager did not always work).  I wonder if things not quite working properly in any of the desktops is specific to nvidia drivers.

---

### Post by anders_c_ on 2010-12-25
Continued updating and now its back to normal! =)

---

