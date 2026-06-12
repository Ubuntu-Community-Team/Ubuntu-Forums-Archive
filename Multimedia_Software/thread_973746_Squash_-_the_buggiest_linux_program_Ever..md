---
title: "Squash - the buggiest linux program Ever."
date: 2008-11-07
forum: Multimedia Software
---

### Post by kooldino on 2008-11-07
Where do I start with this epic turd?

Squash is a batch image resizer.  Something that, quite honestly, should be built into KDE.

Well, the first time I went to use it, I went to resize a bunch of images on my ntfs formatted data drive.

I tunneled down to the desired directory and selected all of the JPG files in that directory so that I can "add" them to the list of files to act upon and then resize them.  

However, it reported the first file in the list could not be found.  I tried again, but this time, it couldn't even see that disk.  It somehow unmounted that disk.  By the way, this killed a large backup that I started 23 hours ago.  Thanks a lot, Squash!

So after rebooting the machine, I quickly learned that simply selecting all of the JPGs in this directory will always result in me losing that drive.  Great.

So for grins, I just chose a handful of the files in that folder.  They added themselves to the list.  Then, just to attempt to trip it up, I went and re-added one of the files that was already added to the list.  Guess what?  I now had two instances of the same file in the list...it wasn't even smart enough to tell me I was an idiot.  I went ahead and removed the duplicate and attempted to resize the selected images, and had set a valid output path for them.

The program locked.  I had to manually kill it.

This is actually the short version of this story, but suffice it to say that this program is awful.  I can't wait to uninstall it.

In the meantime, does anyone know of a nice batch image resizer?

---

### Post by kooldino on 2008-11-07
Command line resize (although I'd prefer a GUI)...

[http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux](http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux)

---

