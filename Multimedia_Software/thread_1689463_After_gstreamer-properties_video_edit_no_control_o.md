---
title: "After gstreamer-properties video edit no control of xwindows"
date: 2011-02-16
forum: Multimedia Software
---

### Post by wiggie on 2011-02-16
I'm not sure this is the cause, but after I changed the properties of gstreamer, by following a fix on VLC freezing during video playback, I cannot control my desktop anymore. Luckily I can still switch windows thanks to docky. Unfortunately I cannot change the tab in the gstreamer-properties so I can reset my change. I changed the video from default to X11.

How can I edit it manually from the command line?

If you think this is not the problem, then what could be it???

Thanks

PS. Ubuntu 10.10 and compiz

---

### Post by BicyclerBoy on 2011-02-17
You can run in a terminal

gstreamer-properties

Or do you mean you have no Gnome GUI desktop..

VLC does not use gstreamer at all.
 
You configure VLC's video output device in the preferences or from cmd line.
Totem uses gstreamer along with lots of std 10.10 stuff.

---

### Post by wiggie on 2011-02-17
I do have gui, but it's unusable. I cannot click on anything. I can use commands like ctrl+t to open a terminal, but alt+tab doesn't switch windows, and clicking on applications or system or whatever doesn't do anything, it's like I'm clicking on a picture of my desktop. It has no effect whatsoever.

Ok, nevermind. I turned it off overnight and now I started it back up again, and now it works. I have no Idea what happened. Really strange.

Thanks for the help. I'll mark this as solved, even though I don't know how it got solved and why it happened in the first place.  Computer voodoo...

---

