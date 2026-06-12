---
title: "No Video"
date: 2008-02-28
forum: Multimedia &amp; Video
---

### Post by Sveet on 2008-02-28
i have VLC and the default media player that comes with 7.10, and they both worked before, but recently, i dont know when, they stopped giving me video. i get sound perfectly fine but no video output.

---

### Post by ubuntu-freak on 2008-02-28
Have you tried MPlayer? Did it happen after xserver or your graphic drivers were updated? Go to System>Preferences>Appearance>Effects and turn them off completely, then try videos again.
 
Also, visite my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and do part 1, just incase you're missing anything you might need. If you still have issues, use the "sudo apt-get --reinstall install" command and reinstall gstreamer and w32/64codecs (whichever is relevant).
 
Hope that helps.
 
Nathan

---

### Post by Sveet on 2008-02-29
im gonna feel really stupid asking this, but how do you paste to command line. ive been looking for it (and i dont feel like typing all that out) but the only thing ive found was shift insert which didnt work.

---

### Post by 3rdalbum on 2008-02-29
You paste into a terminal using Control-Shift-V.

Another thing you could try is, in the VLC preferences, changing the video output driver to "X11".

---

### Post by Sveet on 2008-02-29
thank you, changing it to X11 solved it :)

---

### Post by ubuntu-freak on 2008-02-29
> **Sveet said:**
> thank you, changing it to X11 solved it :)

 
No no no. Don't stick with x11. I could've told you that, but x11 is awful. Did you try disabling effects first? What graphics device do you have?
 
You wanted to paste the commands from my [how-to](http://ubuntuforums.org/showthread.php?t=661833)? I just right-click and select "paste". 
 
You really should get xv (xvideo) working. Your CPU is forced to do all the work if you use x11.
 
Nathan

---

