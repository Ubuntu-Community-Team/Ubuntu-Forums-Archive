---
title: "Changing video mode dynamically?"
date: 2010-07-29
forum: Multimedia Software
---

### Post by Cedders on 2010-07-29
In Ubuntu versions up to 9.04, switching VT with Ctrl+Alt+Fx would switch the adapter video mode between text (console) and graphics (X).  In 10.04 lucid, the console appears to be in the same SVGA graphics mode with a 16x16 bitmapped font.

Is there any utility to restore text mode (eg restoretextmode in svgalib-bin)?  Changing mode or resetting the adapter or changing registers is something that should be easy, even if it screws up X.  I'd quite like the console to be in text mode anyway (VGA mode 7, if I remember rightly), but the main reason is to reset the adapter after what seems to be a bug in the video-ati-radeon mobility drivers.

resizecons won't change mode, and I can't get xvidtune to do anything.  I know the "text" parameter to the kernel stops X and gdm, but again it's using the same bitmapped graphics mode.

---

### Post by Cedders on 2010-08-01
Anyone?  Any command-line utility to reset the graphics adapter and/or change graphics mode?

---

