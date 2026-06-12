---
title: "Screensaver + Remote, first press should only disable screensaver"
date: 2008-11-25
forum: Mythbuntu
---

### Post by funkydan2 on 2008-11-25
Hi,

I'd really like my frontend to be able to have a screensaver when not in use (and that's working really well).  
The 'problem' I have is that, unlike when pressing a button on the keyboard, when the screensaver is running, the first press of a button on my remote (a 'Rock Vista', cheap MCE knockoff) doesn't just disable the screensaver, but it also sends that button command through to mythfrontend.  Thus if I press the 'enter' or 'play' key, it might start liveTV playback, or it might start watching a recorded program, depending on where the cursor is.

I can't seem to find in the xscreensaver setup gui any option that controls what the 'first key press' does.  Is there any way that I can tell either lirc or xscreensaver that the first button press of my remote is just to disable the screensaver, and that I don't want that message sent through to mythfrontend?

Thanks,

Daniel

---

### Post by volkswagner on 2008-11-25
You may want to see how the visualizations (within music player) is handled.  I notice no key (except <ESC> )input will exit the visuals.  Perhaps you can add this function to the screen saver.

---

