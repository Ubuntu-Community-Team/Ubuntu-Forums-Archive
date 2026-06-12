---
title: "Image viewer with copy to clipboard"
date: 2009-04-29
forum: Multimedia Software
---

### Post by schuggiz on 2009-04-29
Hi,

I desperately need an image viewer that supports "copy to clipboard" besides Gimp. Something like gThumb or Gwenview, but it needs that feature. While I am running gnome, I could also deal with KDE-programs.

I heard KView would support that, but i can't find that program anywhere.

Thanks for any help!

---

### Post by jibeddari on 2009-05-06
Hi there,

looking for the same thing myself. It would really improve my workflow if I could use a simple image viewer to select a picture .. and from there use Ctrl+C or drag and drop into OpenOffice.

Best solution so far for me is using Nautilus icon mode for browsing the pictures, and them dragging them into OpenOffice. But it is still cumbersome .. a viewer with clipboard support would be very much appreciated.

---

### Post by no_moniker on 2009-05-14
Yeah I'm looking for that too.  One workaround is to right click the images in the folder and select open with -> open with firefox.  Then you can copy from the web browser.  I'd rather have an image viewer that can do it.  It'd be nice if eye of gnome (the standard ubuntu image viewer) could do it...

---

### Post by btk on 2009-05-22
Following on from the suggestion to use firefox, you can automate it by creating an alias for your shell... say "scrnshot" and point that to execute a script like the one below. 

Firstly:
1. sudo apt-get install imagemagick

Secondly:
1. Create your script:

#!/bin/bash
cd /dmp
rm -rf screenshot.jpg
import screenshot.jpg && firefox /dmp/screenshot.jpg

---

### Post by alfu on 2010-01-08
The Eye of GNOME Image Viewer 2.261 is the best image viewer I have seen yet -- its zoom and pan and preview features are really nice.  I like the way you can just <ESC> out of it.  I don't use Irfanview any more.

That said, I **do** have a wishlist:

1) Copy to clipboard

2) Fullscreen mode is presentation mode.  To navigate in presentation mode *without the keyboard*, the mouse pop-up menu could change between windowed and presentation modes:

[INDENT]A) Right mouseclick: advance to next image
B) Left mouseclick: previous image
C) Left mouseclick & drag: pan image
D) Double-click: return to windowed mode (with its *separate* popup menu)
E) Scrollwheel: zoom (same as it is now)[/INDENT]

3) In presentation mode I often stumble up to the top of the screen, inadvertently activating the menu bar, and have to wait for it to time itself out.  I would like to be able to click anywhere in it (other than the buttons) to shut it off, or just <ESC>.  IMHO, the <ESC> key should **always** be used to get you out of the last established situation.

4) Double-click to toggle between windowed/presentation modes. (This feature went away in 2.281; I would like to see it back) <F11> must be vestigial from some older system for toggling full-screen, and there is no reason to disappear it, but having a mouse-only option would also be nice.

---

### Post by AHands on 2010-12-25
I just now coded two new "clipboard features" into both EyeOfGnome and Shotwell to add "Copy Image" and "Copy Path" to both the "Edit" menu and the right-click menu. I've not yet sent the patches to the package owners though. If you like, I can send you the source patch files, or rpm's for i686. Let me know if you need it in gThumb or anywhere else.

---

### Post by AHands on 2011-01-30
Good news: I submitted my patch to Eye Of Gnome, they accepted and committed it, added their own improvements, and are releasing as eog-2.91.6 !

---

