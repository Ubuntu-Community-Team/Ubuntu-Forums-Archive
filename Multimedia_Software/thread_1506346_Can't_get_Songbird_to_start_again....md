---
title: "Can't get Songbird to start again..."
date: 2010-06-10
forum: Multimedia Software
---

### Post by X-Windows on 2010-06-10
I know, Songbird does not currently support Linux... I got the x64 .deb file off this website ([http://skyzim.com/songbird-1-4-3-installer/](http://skyzim.com/songbird-1-4-3-installer/)) and installed it without issue. I got it up and running then screwed something up with the graphics and needed to reinstall. Now when I get the *same* file off the website, install it, then try to run I get an error "**GLib-ERROR **: /build/buildd/glib2.0-2.24.1/glib/gmem.c:157: failed to allocate 14145530384 bytes**". I tried doing a **sudo apt-get remove libvisual-0.4-plugins** as was recommended elsewhere to no avail. Anyone know how to get songbird up and running again? I did a "Removal" through synaptic to uninstall the first time, perhaps that is an issue?

---

### Post by X-Windows on 2010-06-10
*Sigh...* I hate figuring things out 5 mins after I post. Anyway what I did was to go to /home/username, unhide contents, and delete the .songbird2 folder then run another **sudo apt-get remove songbird.** I've reinstalled and everything *seems* to be working ok. When run from console I'm getting a slew of Gstreamer-WARNING errors but those were probably there earlier too. Mods can lock this post if needed

---

