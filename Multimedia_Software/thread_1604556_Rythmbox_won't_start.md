---
title: "Rythmbox won't start"
date: 2010-10-24
forum: Multimedia Software
---

### Post by raymondvillain on 2010-10-24
Running Ubuntu 10.10.  This problem existed on 10.04.

If I click on Applications>Sound and Video>Rythmbox Music Player a tab at the bottom of the screen says "Starting Rythmbox" and the Rythmbox application opens and the screen is populated with the familiar playlist and controls.  The tab at the bottom changes to read "Music Player" with the Rythmbox emblem.  It looks like I'm about to be able to use it.

But then everything disappears.

Any ideas?

How do I start Rythmbox from a terminal window?

---

### Post by gyussz on 2010-10-24
```
rhythmbox
```

I would try to reinstall it btw.

---

### Post by raymondvillain on 2010-10-24
Thanks for your suggestion, gyussz, but after re-installing it I get the same behavior.

This is what I get when I launch rhythmbox in a command window:
> user@computer:~$ rhythmbox

(rhythmbox:4081): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

(rhythmbox:4081): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
user@computer:~$ 

---

### Post by gyussz on 2010-10-24
Seems like a problem with glib packages. What about reinstall libglib, like
```
sudo apt-get install --reinstall libglib*
```

---

### Post by raymondvillain on 2010-10-24
Well I've partially fixed it.  See this link:

[http://ubuntuforums.org/showthread.php?t=1441600&highlight=rhythmbox+crash]("http://ubuntuforums.org/showthread.php?t=1441600&highlight=rhythmbox+crash")

If I had spelled it "Rhythmbox" instead of "Rythmbox" in the first place I wouldn't have had to post this.

Thanks for the help, anyway.

But now Rhythmbox won't work if there is a CD in the optical drive!  It only works for music files I've already ripped (some time ago with Rhythmbox!) and stored on the hard drive.

Any suggestions will be greatly appreciated.

P. S.  I'm giving up on Rhythmbox.  Just installed Banshee and it works just fine.

---

