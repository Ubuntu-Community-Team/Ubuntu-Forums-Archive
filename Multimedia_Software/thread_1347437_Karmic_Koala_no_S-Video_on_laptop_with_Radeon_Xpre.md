---
title: "Karmic Koala no S-Video on laptop with Radeon Xpress card"
date: 2009-12-06
forum: Multimedia Software
---

### Post by l33t fl33t on 2009-12-06
I have an old HP nx6325 laptop with a Radeon xPress 1150 chip. I'm using the new Karmic Koala release and the Radeon drivers that came were installed by default.

My S-Video works during boot, during startup (while the white Ubuntu logo is loading, all the way to the login screen and then fails) and also on Windows XP. I recall it working on an older release (Intrepid maybe?). Heck, even outputting the console to the TV worked.

I used the files supplied here:
[http://ubuntuforums.org/showthread.php?t=1332157](http://ubuntuforums.org/showthread.php?t=1332157)

The two scripts work somewhat well on their own - the TV finally receives the output but the colors are wrong, especially around text. However, it's still an unsatisfactory solution. Using the supplied Xorg.conf results in failure - instead of output, the screen shows white horizontal lines across the screen. No Linux related S-Video output works anymore.

How do I set it up so that I can switch between TV and built-in LCD via the FN+F4 (which work(s/ed) in every environment except X) without having to bother with all these scripts and hacks?

---

### Post by l33t fl33t on 2009-12-07
Anyone?

---

### Post by Wittank22 on 2010-01-23
I have the same problem.  I used the attached thread solution you mentioned.  It worked for a week.  Now, I am getting the same lines across the screen.  I am using a Compaq V5000 with an AMD Sempron processor and an ATI Radeon xpress 200M.

---

### Post by l33t fl33t on 2010-04-14
In case it helps anyone...

I've managed to make some progress by going to the command line (ctrl-alt-F1) and then running;

sudo atitvout -f t

That displays the command line on the TV (and I can use mplayer to play movies). For some reason, Ubuntu adamantly refuses to do the same in X, even locking up at times with a black screen.

My guess is that the open source ATI driver doesn't handle TV out and, since ATI discontinued support for this particular chipset, that the only alternative for getting the whole thing working more or less properly is to revert to an older release of Ubuntu. Or just go back to Windows, since TV out works there as well as it always did.

---

