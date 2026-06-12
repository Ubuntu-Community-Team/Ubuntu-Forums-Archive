---
title: "Finally got flash working in Flock browser"
date: 2009-02-19
forum: Multimedia Software
---

### Post by illumin8 on 2009-02-19
Flash working in Flock Ubuntu Intrepid
This took me entirely to long to figure out, but I finally got it.
To get flash working in Flock, ( or to transfer any plugin from firefox to flock)

You must first have firefox fully functioning...i.e you must have installed the flash-nonfree plug in, or the SWF plugin.

Once you have this working,

Follow these steps...

in Terminal, enter...

sudo nautilus

Then in a very windows sort of way, navigate  to this  file...

usr/bin/firefox/plugins

Copy the Flash plugin which should be a .so file.

Then navigate to this file...

usr/share/flock/plugins

Paste the copied file/s.

Exit Nautilus...

Start Flock.

Watch Youtube.

---

### Post by hieronymouse on 2009-04-27
I wonder if it's still working for you.  A couple of times I have thought I fixed this problem.  The sound worked, but the next day it was back to square 1.

---

