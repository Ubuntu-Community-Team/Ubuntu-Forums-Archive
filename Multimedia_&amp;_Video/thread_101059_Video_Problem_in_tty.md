---
title: "Video Problem in tty"
date: 2005-12-09
forum: Multimedia &amp; Video
---

### Post by alan_daniel on 2005-12-09
Hey, I am running Breezy on an IBM Thinkpad R31, and everything works fine except for the tty's. The white text is dimmed a little and flashes very frequently. The resolution doesn't seem to be correct, either, as the first line of the tty is well above the display of the laptop. The text is visible at the very top of the display with the top half cut off after hitting enter twice (after two full lines). I had a very similar problem when running debian. The X-server recognizes the video driver perfectly, and there aren't any problems with that. I want to boot into the tty instead of directly to the gdm, however, so this whole tty thing is a bit of a problem.

Anyone know what's going on? Thanks!

---

### Post by afhp on 2005-12-09
Just an idea, but this sounds like the wrong console resolution. 

Note -- I don't know the R31, my experience is with the T21. I suggest you disable video expansion in the BIOS, if the R31 has such an option -- so that during POST, only part of the screen is used. After that, experiment with the boot option "vga=xxx" and whether to load the generic vesafb module, or a hardware-specific one (option "video=xxx").

Best way to do it is probably from the Grub menu at boot-up, where you can edit the boot options directly (type "e" at the menu, I think) ; once you've found the right values, update /boot/grub/menu.lst accordingly to make them stick.

On the T21 (1024x768 LCD), it works fine with the default vesafb module (no "video=..." option) and "vga=791" -- that gives me a nice non-expanded fullscreen console of about 128x48 chars.

---

