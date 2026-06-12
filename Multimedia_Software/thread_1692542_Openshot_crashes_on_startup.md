---
title: "Openshot crashes on startup"
date: 2011-02-21
forum: Multimedia Software
---

### Post by jimbo99 on 2011-02-21
After having used Openshot successfully yesterday today I get the following:


--------------------------------
   OpenShot (version 1.3.0)
--------------------------------
state saved
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtkrecentmanager.c:1942:get_icon_fallback: assertion failed: (retval != NULL)
Aborted


Thoughts?

---

### Post by inobe on 2011-02-21
i am still using version 1.2.2

obviously you are bumping heads with a buggy version.

i think they have a ppa, maybe that will help.

---

### Post by jimbo99 on 2011-02-21
The issue seems to stem from the .osp files.

It appears that the last (or most recent) .osp file, if it is located in the place where you saved it (yes, I'm actually saying that) when you open openshot it will crash (with that error message). 

Another issue that might contribute is that the .osp file is a rather large text file.  Contained within the .osp file are some hard coded paths to a folder that contains some .png snapshots of the first frame of each file that you added to the project.

So, the problem could be with Openshot trying to load some information about the last (or most recent) project(s).

If you move the .osp file to another location you can launch Openshot.  If you try to open the .osp file you moved it will crash.  If you try to open the .osp file in gedit, gedit will crash.

If you open it with nano that works.  There appears to be no corruption.

---

### Post by inobe on 2011-02-21
i will try 1.3.0 and see if i experience this behavior.

---

### Post by inobe on 2011-02-21
i haven't been able to replicate any of those errors, i did find one of my own.

exported videos causes all players to crash, they are unplayable.

---

### Post by jimbo99 on 2011-02-21
> **inobe said:**
> i haven't been able to replicate any of those errors, i did find one of my own.

exported videos causes all players to crash, they are unplayable.

Try deleting the folder on your desktop with the snapshot .png files, and then opening openshot.

Mine was a Bluray creation.  That means it created a .mp4 file.  I did choose highest quality.

---

### Post by kelver69 on 2011-02-22
I gave up on Openshot a few weeks ago.  It had such promise, but crashed way too much for my liking.  I switched to Kdenlive and have never looked back.  It looks a little intimidating at first, but once you play with it for a while, you'll have it figured out.

---

