---
title: "No sound in X after text-based login"
date: 2009-10-12
forum: Multimedia Software
---

### Post by Bit101 on 2009-10-12
After disabling GDM to login from console, sound no longer works in X. If I try playing a soundfile in Gnome after logging in using TTY1 and doing startx, no sound works. However, going into TTY1 (or any other TTY) and typing in ```
cvlc <musicfile.mp3>
``` plays sound fine.

---

### Post by yabbadabbadont on 2009-10-12
Just to check for the obvious, have you checked your sound mixer settings to be sure that they aren't muted or set to zero?  Also, while in Gnome, if you open gnome-terminal and run "cvlc <musicfile.mp3>" does it still produce sound?

---

### Post by Bit101 on 2009-10-12
[s]Never mind. Problem seems to have fixed itself.[/s]
EDIT: Never mind, problem persists.
Mixer settings are at full, and gnome-terminal doesn't make sound either. However, I found that if I first started GDM, logged in, logged out, killed GDM, then started X with startx from TTY1, I get sound. However, logging out completely( No GDM,No X, all TTYs logged out), then logging back in to TTY1 and doing startx gives me no sound in X as origional post states. I'm assuming there must be some service GDM starts up that allows connecting sound to X?

---

### Post by Bit101 on 2009-10-13
Bump

---

