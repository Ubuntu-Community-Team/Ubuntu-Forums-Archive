---
title: "MCC starting at boot up, needing a password.??"
date: 2009-11-20
forum: Mythbuntu
---

### Post by AlecJ on 2009-11-20
I'm getting Mythbuntu control center starting up at boot up, it puts a password box up and waits for an input, preventing the frontend from starting up. This password box can not be removed with the remote, so I have to VNC in and clear the box.

I can't find where it is being called from or why it's starting at all, it started before Xfce has put the "Applications" label at the top of the screen.

It started doing this after a clean install Mythbuntu 9.04 amd64 with Myth .22 and using MCC.

Anyone got any ideas?

---

### Post by klc5555 on 2009-11-20
Try clearing the MCC window, and, with no extraneous windows open, log out of X, making sure to check "save settings on exit". Hopefully, MCC will be gone next time X respawns.

---

### Post by AlecJ on 2009-11-26
Cheers, that worked.

---

