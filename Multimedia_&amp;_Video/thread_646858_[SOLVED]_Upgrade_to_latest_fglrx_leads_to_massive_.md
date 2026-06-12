---
title: "[SOLVED] Upgrade to latest fglrx leads to massive WTF"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by insert_name_here on 2007-12-21
I just updated to the latest fglrx (7.12).  I downloaded the ati-whatever.run, and ran it with "sudo sh ati-whatever.run --buildpkg Ubuntu/gutsy" which made some .debs and installed them.  

Upon restarting, not everything fits on the screen.  If I move my mouse to the left or bottom of the screen, some bits show up that I couldn't see before.  That is, I can see EITHER the top gnome taskbar OR the bottom.  They won't both fit. 

My screen res is 1400 x 1050... Any ideas?

---

### Post by hedgebox on 2007-12-21
I had a similar problem after I upgraded. My desktop extended way off to the right as if there was a second monitor. I was using the same xorg.conf file as before. I could not find anything wrong with that or anything else so I just uninstalled it for now.

---

### Post by insert_name_here on 2007-12-21
Wait... hmm.. That didn't work.

---

### Post by kelvin spratt on 2007-12-21
Try using Envy to download and install the latest drivers for ATI and Nvidia

---

### Post by fiatguy85 on 2007-12-21
Does Envy install the latest version 7.12?

The problem occurs for me also when I'm trying to run 1680x1050 resolution using the same xorg.conf that was previously working at that resolution.  It only will run 1280x1024.  It works alright on my laptop running only 1280x800 although on both computers I also noticed a flickering on the monitor during power state changes.

---

### Post by darrell on 2007-12-21
Radeon Xpress 200M here. Very interested in the new driver for this GPU - can use direct rendering and apparently suspend/hibernate issue is solved. 

However, after installing it, I cannot get my bigdesktop to work as it does under the fglrx from the repos - it almost works, but my second screen size in xorg.conf is ignored, and the second screen can only be run at the same as the laptop monitor - 1280x800 instead of 1440x900, unlike the fglrx in the repos which is quite happy with different monitor resolutions.

As running an LCD at an alien resolution results in an almighty mess of a display, I've reverted to the ubuntu repo version for now.

Any ideas anyone?

---

