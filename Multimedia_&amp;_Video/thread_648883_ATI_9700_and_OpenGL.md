---
title: "ATI 9700 and OpenGL"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by mau84 on 2007-12-24
I have Gutsy and a Ati Mobility 9700. It works wery well with restricted driver, so Compiz run fine, BUT when I use glxinfo I read
> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

So I suppose HW acceleration desn't work, infact when I try to run a simple program using OpenGL library...x-server crash and I see all screen black.
What I have to do to enable Dri? In xorg.conf I have disabled composite as read in some post, but dri ddoesn't work.

---

### Post by acoustibop on 2007-12-24
What driver are you using, mau84?  At a guess, since you say you're using "restricted driver" and you have Compiz working, it must be one of the recent 2 or 3; in which case, it should support Composite and that shouldn't be disabled.

What do you get for fglrxinfo?

---

### Post by NineseveN on 2007-12-27
I'm getting the same thing, and none of the games I've tried will render right (Nexuiz, Open Arena, Suaerbrauten etc...) on a 9600 PRO.

---

