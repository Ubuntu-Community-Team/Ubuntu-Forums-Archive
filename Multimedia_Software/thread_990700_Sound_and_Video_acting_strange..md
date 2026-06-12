---
title: "Sound and Video acting strange."
date: 2008-11-23
forum: Multimedia Software
---

### Post by Arukas on 2008-11-23
Most of the time, my sound and video work when watching movie clips.  (except for streaming video, but I'll ask about that later) 

One thing I notice, I download things from the megadownloads. I notice if firefox is open tot that page, my sound on Ubuntu will not play.  What's going on and can that be fixed?  It just seems like it don't like to multi task very well.  

-Arukas

---

### Post by Arukas on 2008-11-23
So I take it, this is not a common problem at all?

---

### Post by alcapone-g on 2008-11-24
If it happens only in a web browser like firefox you have to do:
From Synaptic Package Manager

Any flash has to be uninstalled example:
gnash
swfdec-mozilla
or a libery supporting flash.

and than install :
flashplugin-nonfree 
flashplugin-nonfree-extrasound.
Embeded video in firefox starts working.

---

### Post by psyke83 on 2008-11-24
> **Arukas said:**
> So I take it, this is not a common problem at all?

Yes, it is. Your PulseAudio configuration is not optimal.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

