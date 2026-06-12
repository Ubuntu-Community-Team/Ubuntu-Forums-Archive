---
title: "help with screen resolution"
date: 2008-09-08
forum: Multimedia Software
---

### Post by eternaldeals on 2008-09-08
I just installed Ubuntu 8.04 and I have an nvidia 6200 video card
all I can get is a resolution of 640x480 I installed the nvidia drivers with envy. I cannot change anything please help.

---

### Post by steevk on 2008-09-08
This is actually quite similar to a problem I'm having, so I figure I'll post here with a bit more information. It's probably relevant to both of us.

So I installed Hardy, no problem. Things seemed to be working fine, except that I noticed that the proprietary driver wasn't showing up. I usually use the proprietary one from Nvidia (I have a 9600GSO) so I installed it. Now I only get 800x600 max resolution. I've tried changing the driver from nvidia to just nv, to vesa, to vga, I've tried automatically reconfiguring my xorg.conf using both dpkg-reconfigure and nvidia-...whatever it was called. I forget. Anyway, I'd like some advice too.

---

### Post by oldrocker99 on 2008-09-08
I have noticed that if you hit ESC when GRUB starts to load, and select diagnostic mode, you should eventually be presented with the opportunity to reset the XServer. Try that.

Also:

sudo displayconfig-gtk

Select your monitor from its tab, and your card and driver from the other tab (select). Log out, and things should be where you want 'em.


Good luck!

:guitar:

---

### Post by eternaldeals on 2008-09-08
> **oldrocker99 said:**
> I have noticed that if you hit ESC when GRUB starts to load, and select diagnostic mode, you should eventually be presented with the opportunity to reset the XServer. Try that.

Also:

sudo displayconfig-gtk

Select your monitor from its tab, and your card and driver from the other tab (select). Log out, and things should be where you want 'em.


Good luck!

:guitar:


Thanks for the help oldrocker99
that fixed it I did the sudo displayconfig-gtk   
and it let me select my card and set the resolution then I loged out and back in and all is working.
thanks

---

