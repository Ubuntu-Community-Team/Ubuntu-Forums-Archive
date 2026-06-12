---
title: "Rythembox Crash?"
date: 2010-12-16
forum: Multimedia Software
---

### Post by MAFoElffen on 2010-12-16
Ubuntu 10.10 Desktop Edition 64 Bit.

Was Running fine.  Everything worked great. Then... hadn't used in a while- Tried to start it up, the window was coming up like it was loading and PUFF!!! Gone. Window of Rhythembox went away.

Now it does this everytime I try to start it up.  The "speaker" icon applet has "Rythembox" in it's menu, but it only does the same thing.  Sound preferences does not show it as using any sound resources nor does the system monitor show it as any running processes...

I tried to reinstall from the Synaptic Package manger and it reinstalls with no errors, but no love on getting it working again.

Anyone have any ideas on this?

---

### Post by Yellow Pasque on 2010-12-16
Start rhythmbox from the terminal. Maybe it will crash with an error message and give you something more specific to search with.

---

### Post by MAFoElffen on 2010-12-16
Here are the errors from a command line:
```
mafoelffen@maf-ubuntu-01:~$ rhythmbox

(rhythmbox:6238): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
** (rhythmbox:6238): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:6238): DEBUG: Loading the real store page

** (rhythmbox:6238): WARNING **: Got less number of items in credentials hash table than expected!
** (rhythmbox:6238): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token
Segmentation fault

```

Hmm... Is there a cfg file for this somewhere that might be corrupted or missing?

---

### Post by Yellow Pasque on 2010-12-16
Hmm.. a segfault. It looks like it might be caused by the Ubuntu One Music Store plugin (this is a common issue). Try removing it:
```
sudo apt-get remove --purge rhythmbox-ubuntuone-music-store
```
If you can start rb normally after that, you've found the issue. If not, you might want to install rhythmbox-dbg and gdb packages, and find a help guide on obtaining a backtrace with gdb. This should give you a more specfic error to search for, or at the very least, help you produce a meaningful bug report.

---

### Post by MAFoElffen on 2010-12-17
It started and stayed running... but not before getting these errors:
```
mafoelffen@maf-ubuntu-01:~$ rhythmbox

(rhythmbox:6535): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

(rhythmbox:6535): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


```
It does still have all my settings and preferences from before... as well as seeing the previously created playlists.

---

### Post by christianco on 2011-01-06
Same problem here, after removed Ubuntu One, same error, occasional sudden quits.

---

