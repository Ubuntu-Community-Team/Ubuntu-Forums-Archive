---
title: "err: The X11 driver is missing."
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by yaronshani on 2006-12-21
i have graphic card ati radeon x550xt
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700/X550 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

and i have problem with wine
when i run exe file with wine , wine say

The X11 driver is missing.  Check your build!

someone can help to solve the problem please?

---

### Post by iansane on 2007-10-12
ok this is sad. I'm having the same problem. Can't even run winecfg or winefile from terminal or from the menu icons. Nothing happens. "x11 driver is missing, check your build" I notice the last post is Dec. of 2006. It's almost a year later and I'm having the same problem and no one has answered this guys post? At several linux and ubuntu forums, I'm finding similar posts but no answer. Somebody please help. :)

Oh and before someone says it, Envy does not fix the problem. It wants to install the video driver which is alredy installed and working fine.

---

### Post by Taddy on 2007-11-24
I'm having the same problem.
I solve it.
1. download wine source-code from winehq.com
2. extract it
3. run the following commands to build Wine:
./configure -v
"-v" will show you the missing Packages for example
> configure: WARNING: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need to install
development packages of Xlib/Xfree86 at the very least.

configure: WARNING: FontForge is missing.
Fonts will not be built. Dialog text may be invisible or unaligned.

Configure finished. Do 'make depend && make' to compile Wine.

=> install  Xlib/Xfree86 and FontForge
4. make depend
5. make
6. make uninstall     (uninstall old version wine)
7. make install

that helped me

P.S.
sry for my bad English

---

### Post by SugarBlush on 2007-12-08
Can you pls be more specific. Do you know where I can get Xlib/Xfre86?? and how do you install it?

---

