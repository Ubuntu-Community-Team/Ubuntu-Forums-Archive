---
title: "ATI Rage video noise problem"
date: 2009-09-22
forum: Multimedia Software
---

### Post by klugja on 2009-09-22
I was running Windows 2000 on my old Dell Inspiron 4000 laptop.  It was fine, but sluggish.  I saw no video problems with Windows.

I have kernel 2.6.28-15-generic #49-Ubuntu SMP and:

ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

I am seeing hash marks dancing from bottom to top on the right side of the screen.  They are more visible when the screen is dark.  Adobe Flash is particularly annoying.

Also, if I hibernate, then bring the PC back, I get an X login screen that says I have timed out, and it is unresponsive.  If I then go to a console screen, it is slow getting there.  The X login screen has garbage at the top.  If I restart X, it does not fix the problem.  I have to reboot.

---

### Post by klugja on 2009-10-04
I tried Fedora, and same exact problem.

I installed opensuse 11, and it defaulted to 800x600, just like ubuntu, but there was no noise.  I then found I could configure 1400x1050#60Hz with 16.7million colors and still no noise.

Too bad Sax2 won't go into ubuntu.

I suspect Ubuntu does not have the right configuration for my controller/display.

So should I say Solved?

---

### Post by klugja on 2009-10-14
I didn't like the performance of Youtube on OpenSUSE, so I decided to try the xorg.conf file from OpenSUSE.  It worked!  So now I have ubuntu working with no rolling noise.:P

I uploaded my SaX created xorg.conf file.  It is for a Dell Inspiron 4000 with Rage Mobility M3 AGP 2x (rev 02) and its flat panel display.

---

