---
title: "Floola Crashes on Startup, little debug info given"
date: 2009-01-28
forum: Multimedia Software
---

### Post by tomsa on 2009-01-28
I have been having some trouble with Floola and my Ipod.  I am using Ubuntu 8.10 and a 120 GB Ipod Classic (6 gen, I think).  I haven't really had any trouble with it until recently.  When I connect my ipod, the software starts, loads to anywhere from 70 to 100%, and then crashes.  Sometimes when I eject my Ipod after this happens, the Ipod tells me there is nothing on it, but when I remount the Ipod, all my files are still there (thankfully).  The only way I have been able to get it to work is to open floola without the ipod connected, let it tell me it can't find my ipod, quit floola, mount my ipod, and then open floola again and it seems to work.  The only other thing I can think of that crashes it is when I try to use the photo management tool, but I think I'm just going to try and remove all of the photos from my Ipod at this point.  The following is the only real pertinent information I can think of:   

I have tried upgrading my floola to version 4.7.

When I try to launch floola from the terminal the output it gives when it crashes is "Segmentation Fault"

If I get it to run from the terminal, when I close the program I get the following output:

```
(Floola:8847): Gtk-CRITICAL **: gtk_window_set_transient_for: assertion `window != parent' failed
Segmentation fault
```   

I have no real idea what any of this means.  Any advice would be helpful.  I'm fully aware of the existence of rockbox, gtkpod, amaraok, rhythmbox, banshee, etc. I haven't gotten to that point- yet.  I'd like to try and fix this before I just go to something different so that I might learn something.  Thanks for the help.

---

### Post by kostkon on 2009-01-28
Hmmm, it's difficult to tell what is causing these crashes. 

Floola is a closed source application and thus it is difficult to figure out what is going wrong (for example, I don't even know what language is Floola written in or what libraries it's using).

I think the best solution would be to send your description here as a bug report to the Floola developer.

The problem/bug may be fixed in the next version. And since Floola is updated often, you may not have to wait for long...

Hope that helps.

---

### Post by tomsa on 2009-01-29
I wasn't aware that Floola was closed source.  Thanks for informing me of that fact, and the advice!

---

