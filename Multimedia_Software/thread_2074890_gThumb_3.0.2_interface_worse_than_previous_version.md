---
title: "gThumb 3.0.2 interface worse than previous version"
date: 2012-10-22
forum: Multimedia Software
---

### Post by Mozai on 2012-10-22
I used gThumb to help manage my bountiful image collection, but the new version 3.0.2 that comes with Ubuntu 12.10 has some changes to the interface that seems awfully inefficient.

* There is a larger margin around each thumbnail (20-30px, for 60px of non-usable space between items), no matter what thumbnail size I choose.
* The File Properties area cannot be toggled off, and it is much larger than before; furthermore, it is present even when no image is selected and thus cannot display useful information.

I would like to know how (without forking gThumb and writing new source code) to do the following:
* **shrink the gap between thumbnails** to something less wasteful, either as a constant ("6px margin around each thumbnail") or a percentage ("5% of thumbnail size -> 6px between 64px thumbnails, 13px between 128px thumbnails")
* **eliminate the File Information part until I ask for it** of the browsing interface; perhaps as something I could summon when I am looking at a single image.  At the very least, the File Information part should only appear when one (and only one) image is selected in the browsing interface.

I hope I can attach an image to help indicate what I'm talking about in case I am not clear.

[IMG]http://i.imgur.com/irmlW.png[/IMG]

---

### Post by mjc1 on 2012-10-22
I do not think those are configurable. Ask the developer about it at:

[https://mail.gnome.org/mailman/listinfo/gthumb-list](https://mail.gnome.org/mailman/listinfo/gthumb-list)

---

### Post by LewisTM on 2012-10-22
In version 3.1.2 you can toggle the properties pane with View->Properties (Ctrl-I), or by clicking the button at the top right. The icons have the same spacing though.

You can get it from the general Webupd8 PPA or the specific one about GThumb
[https://launchpad.net/~webupd8team/+archive/gthumb](https://launchpad.net/~webupd8team/+archive/gthumb)

---

