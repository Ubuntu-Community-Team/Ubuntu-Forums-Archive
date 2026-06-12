---
title: "Ctrl-alt-backspace doesn't do anything, I want it back"
date: 2009-10-09
forum: Mythbuntu
---

### Post by mgrusin on 2009-10-09
Hello, I just updated my MythTV box to Mythbuntu 9.04. This was a complete reformat and reinstall.

As with the last version I was running, my frontend will freeze up from time to time.  This isn't a huge problem, since the backend is solid and keeps recording while I simply restart the frontend.

What is a problem is that in my last version I could easily hit "ctrl-alt-backspace" on my wireless keyboard to restart X and the frontend.  In this version, ctrl-alt-backspace doesn't seem to do anything. "Ctrl-alt-del" will leave me with a locked-screen dialog, from where I can get to a screen that lets me restart the whole computer, but that kills off the backend too.

There is a similar problem with exiting MythTV.  It leaves me at the desktop, but I can't do anything useful from the keyboard unless I plug a mouse into the computer and open a terminal or choose a menu option etc.  I'd much rather just hit ctrl-alt-backspace and have everything restart itself.

QUESTION: is there an easy way to get the "ctrl-alt-backspace" functionality back for my system?

Thanks! -Mike Grusin

---

### Post by sisco311 on 2009-10-09
try: Right Alt + PrintScreen (SysRq) + k

or install the dontzap package and run:
```
sudo dontzap --disable
```

---

### Post by klc5555 on 2009-10-09
> **mgrusin said:**
> Hello, I just updated my MythTV box to Mythbuntu 9.04. This was a complete reformat and reinstall.

As with the last version I was running, my frontend will freeze up from time to time.  This isn't a huge problem, since the backend is solid and keeps recording while I simply restart the frontend.

What is a problem is that in my last version I could easily hit "ctrl-alt-backspace" on my wireless keyboard to restart X and the frontend.  In this version, ctrl-alt-backspace doesn't seem to do anything. "Ctrl-alt-del" will leave me with a locked-screen dialog, from where I can get to a screen that lets me restart the whole computer, but that kills off the backend too.

There is a similar problem with exiting MythTV.  It leaves me at the desktop, but I can't do anything useful from the keyboard unless I plug a mouse into the computer and open a terminal or choose a menu option etc.  I'd much rather just hit ctrl-alt-backspace and have everything restart itself.

QUESTION: is there an easy way to get the "ctrl-alt-backspace" functionality back for my system?

Thanks! -Mike Grusin

Since nobody ever needs to zap X in Ubuntu (ahem) the three finger zap was removed by default.

The preferred way to put it back in is to install the package "dontzap":  

sudo apt-get install dontzap

And then disable dontzap from "dontzapping":

sudo dontzap --disable

Then log out one last time and restart X, and upon X restart ctl-alt-backspace should once more be doing what it ought to be doing.

---

### Post by mgrusin on 2009-10-09
Thanks very much for the reply!  Right_alt-printscreen-k definitely does what I want.  I'll try to remember that (my fingers know ctrl-alt-bs by heart after all these years).  Did something change, or was that key combo always there?

I'll look into dontzap as well.

Thanks again, that's great! -Mike Grusin.

EDIT: didn't see the second reply before I responded to the first, that answers my question about what happened to ctrl-alt-bs.  I'll definitely look into dontzap.  Thanks very much everyone!

---

### Post by sisco311 on 2009-10-09
> **klc5555 said:**
> Since nobody ever needs to zap X in Ubuntu (ahem) the three finger zap was removed by default.



The ctrl-alt-backspace key combination was disabled because of a upstream (X.org) design decision:

> The Ctrl-Alt-Backspace key combination currently "zaps" (hard-restarts) the X server, and thus loses any unsaved data in applications, etc. This key combination is also largely undocumented, so users (probably ex-Windows users) may press this key combination without expecting data loss. This spec proposes to follow upstream's lead and disable this key combination by default in order to prevent this usability issue from occurring in normal installs.

---

