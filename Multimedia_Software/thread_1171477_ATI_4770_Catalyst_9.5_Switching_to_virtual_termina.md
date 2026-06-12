---
title: "ATI 4770 Catalyst 9.5: Switching to virtual terminal freezes system"
date: 2009-05-27
forum: Multimedia Software
---

### Post by days_of_ruin on 2009-05-27
If I switch to a different tty (like ctrl+alt+2) the whole os freezes
and the screen is black. Unable to ssh in from another computer and I have to do a hard shutdown. Has anyone else has this problem and is there a way to fix it?

---

### Post by jmfrank63 on 2009-05-29
I'm having the same problem with my 2 4830 and 9.5. Black Screen with artifacts, as soon as i am using a framebuffer. Works without framebuffer.
Due to necessary hard resets shot my /etc directory and had to reinstall. Thought it was for the crossfire chain. Had it working with ubuntu supplied drivers (the restricted ones). Very difficult problem to debug, because of the freezes one cannot supply any logs.
for your problem try to remove framebuffer vga= from menu.lst.
9.5 seems realy dangerous.

---

