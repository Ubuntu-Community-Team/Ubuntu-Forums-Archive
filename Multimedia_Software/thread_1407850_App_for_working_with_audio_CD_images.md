---
title: "App for working with audio CD images?"
date: 2010-02-15
forum: Multimedia Software
---

### Post by Objekt on 2010-02-15
Is there a Linux app for mounting and playing audio CDs from image files?  I have saved disc images of nearly all of my CD collection, but I have yet to find any convenient way to play them.  

Because of the nature of CD audio, every CD image has an accompanying .cue file, so there are actually 2 files (*.iso or *.bin and *.cue)  from each disc.  VLC Media Player will play DVD .iso images directly, but doesn't know what to do with audio CD images (or the .cue files).

Mounting and unmounting the images at the command line is tedious, given the very long file paths.  I'd rather have a GUI-based app.  Does any such thing exist for Linux?

FWIW, Acetone ISO doesn't work.  It doesn't want to mount my *.iso format CD images.  Probably some funkiness of the CD audio format.  I think it is what the Acetone devs call a "multi-sector image."  Likewise for the *.bin images of CDs.

---

### Post by Objekt on 2010-03-01
Bumpity.  I really need a solution to this one.  I don't want to go on archiving my audio CDs in a format I can't use under Linux.  Unfortunately there does not appear to be any way to neatly store an image of an audio CD in a single file, as can be done with DVDs.  Or maybe I'm just doing it wrong.

---

### Post by mc4man on 2010-03-01
I'm not too sure that anything will play audio cd's in bin/cue directly without mounting (don't have any in .iso form

As far as mounting that can be made easier in a couple of ways - I use cdemu to mount ([ppa here]("https://launchpad.net/~cdemu/+archive/ppa")

For actually mounting a bin (using the .cue), I just use a nautilus action so a simple right click on the .cue mounts it

As far as players here I use amarok 1.4 (or pana redo), I have it set up thru the use of a script to autostart / autoplay cd's from any drive - which would include the virtual one created with cdemu

---

