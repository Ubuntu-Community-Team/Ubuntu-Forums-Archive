---
title: "Creative Zen Vision:M"
date: 2008-05-07
forum: Multimedia Software
---

### Post by shakabra on 2008-05-07
Before Hardy came out I tried out the beta version from the Live CD.  When I plugged in My Creative Zen an icon appeared on the desktop.  The Zen was visible to my computer.  I have had Hardy installed for a couple of weeks now.  I have installed mtptools, libmtp... but the only way I can access my Zen file is using Gnomad2.  Does anyone have a clue why?  It's not really a big deal but I liked being able to see the Zen on my desktop and look at the files from there.

---

### Post by insert_name_here on 2008-05-08
run this once:

sudo mkdir /media/zen

and every time you connect the zen to the computer:

mtpfs /media/zen

and right before you disconnect,

sudo umount /media/zen

Sorry it's not automatic, it probably can be done with some plug/unplug event, but I don't know how to do that.  By the way, Nautilus doesn't seem to like MTP devices and disconnects often when you try to modify files that way.  The command line, for some reason, doesn't crash like this.

---

