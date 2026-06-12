---
title: "Ubuntu/XP Dual boot--XP won't recognize wireless card. Pls help!"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by HamaLee on 2009-02-28
I've been having trouble with my 3495ABG wireless card (as are many others) so I decided to install a dual boot so I can go back to Windows XP til I can figure out how to fix things.  I love Ubuntu and I loathe the idea of going back to Windows--but I haven't had any luck whatsoever trying to fix the wireless issue.

So I followed this tutorial to set up my partitions: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

The current problem: In XP the computer does not recognize ANY wireless card or ethernet card.  I tried to install the appropriate wireless driver and an error message popped up saying there isn't enough room on /C, which seemed weird.  So I looked and realized that in the Windows partition the hard drive is actually /F. This was briefly mentioned in the tutorial but not how to fix it. I tried to just change the intended location of the driver to the F drive, but that didn't work.

Anybody have any ideas on how I can resolve this?

(Obviously--I'm a noob.  I've tried searching the forums for something that can help me but I haven't been able to make heads or tails.  If you can link me to a better thread or tell me how to resolve the problem it'd be much appreciated.)

---

### Post by abfan1127 on 2009-04-12
Have you tried changing the drive letter from F to C?

---

