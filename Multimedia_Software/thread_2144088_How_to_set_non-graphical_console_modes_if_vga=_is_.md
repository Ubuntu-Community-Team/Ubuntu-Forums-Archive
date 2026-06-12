---
title: "How to set non-graphical console modes if vga= is deprecated"
date: 2013-05-11
forum: Multimedia Software
---

### Post by carangil on 2013-05-11
Hi, I'm using an nvidia card, so I am using nomodeset, which drops me down to the basic BIOS mode when I'm not in X.  That's fine, 80x25 is classic IBM PC hardware text mode.  In the old days of linux, you could put vga=0xf01 on the options list, and get in 80x50 text mode.  How do I do that in Ubuntu 12.04?  


[LIST]
[*]The old 'vga=' option doesn't appear to be available anymore.
[*]I'm supposed to use gfxmode, but that only takes parameters such as 800x600, etc, actual graphics modes.
[/LIST]

Is it currently impossible to set 80x50 true text mode on Ubuntu 12.04?

Thanks!

---

### Post by 2F4U on 2013-05-11
I don't know if you will be able to set 80x50, but you can set a different resolution for the tty console:

[http://blog.mattrudge.net/2012/10/02/changing-the-tty-resolution-on-ubuntu-server/](http://blog.mattrudge.net/2012/10/02/changing-the-tty-resolution-on-ubuntu-server/)

---

### Post by carangil on 2013-05-13
Cool thanks, that did work!  This isn't true 50 line mode, but I don't really care, I just wanted more lines if I happen to be in before X starts.  I still am curious what it would take to go to 80x50 short of hacking grub2 or going back to old grub.

I didn't think I could use nomodeset and GRUB_GFXMODE at the same time.  I thought nomodeset means no graphics at all.  Turns out nomodeset just keeps the kernel from changing the modes.  Whatever grub set it to will be kept.

GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD=keep
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

When X loads, the nvidia evil binary blob takes over and I get full acceleration.  And CTRL-ALT-Fx console still seem to work.

[FONT=arial][/FONT]

---

