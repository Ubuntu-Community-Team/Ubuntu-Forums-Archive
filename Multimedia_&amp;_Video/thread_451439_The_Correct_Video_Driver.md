---
title: "The Correct Video Driver"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by picosam on 2007-05-22
I'm a beginner and I'm confused; please help me out! I have a Gigabyte motherboard with a built-in Intel video card chip. I installed Ubuntu 7.04 and it's working successfully with the card. I upgraded to the intel driver (instead of the i810 driver) and it still works fine. The problem is it's too slow. Is this the optimum the system can be configured to? When I click on the log off button (for example) I have the screen literally redrawing the background to shade it (like what we have on Windows when the drivers *aren't* installed). Is there something I can do to make this better?

Thank you,
Sammy

---

### Post by steevols on 2007-05-22
Is 3D acceleration working? It sounds like you're using software rendering.

---

### Post by picosam on 2007-05-22
I'm sorry, but how do I find out if it's working/turn it on if it isn't?

---

### Post by picosam on 2007-05-22
Well, I ran glxinfo and I have direct rendering set to yes.

---

### Post by steevols on 2007-05-22
Well, an easy real-world test would be to open Screensaver Settings and see if a 3D screensaver will run at a high framerate.

Oh, why can't you just go back to the original driver?

---

### Post by picosam on 2007-05-22
I tried a 3D screensaver, it worked very well! The original driver has the same problem. I think my problem is in the 2D, not 3D. Is there anything extra I should put in the xorg.conf file (like AGP settings or something)?

---

### Post by steevols on 2007-05-22
Well, I'm all out of knowledge on this one. Sorry!

---

### Post by dabl on 2007-05-22
I saw a post recently that mentioned that Intel video chip needs to share memory with your CPU.  There needs to be a line in xorg.conf that sets at least 16 MB of RAM for use by the video system, if I'm remembering it correctly.  Probably if you search on "GMA 915 xorg.conf" or whatever the chip model is, you can find more about that.  ;)

---

### Post by picosam on 2007-05-23
Here's my video log, hope it would help identify the problem: [http://paste.debian.net/28645](http://paste.debian.net/28645)

---

### Post by dabl on 2007-05-23
Pico, I think your answer lies herein:

[http://ubuntuforums.org/showthread.php?t=451719&highlight=video+ram](http://ubuntuforums.org/showthread.php?t=451719&highlight=video+ram)

:D

---

