---
title: "VLC fullscreen control panel missing"
date: 2008-12-17
forum: Multimedia Software
---

### Post by 11010110 on 2008-12-17
hi everyone, 

I have been enjoying VLC media player for movies and the like and recently after clicking pause on it, the full screen control panel (the one that pops up when you use the mouse in full screen mode) disappeared! I really love this feature and i was wondering if anyone knew how to get it back. 


Thanks for any help in advance!

---

### Post by 11010110 on 2008-12-18
nevermind enough tinkering eventually fixed it.

---

### Post by Gausian on 2008-12-18
Please share your solution so that others may gain from your experience.

---

### Post by hemcii on 2008-12-30
I got that problem too and found a solution to it.
ive opened the file vlc-qt-interface.conf in /home/username/.config/vlc
nano .config/vlc/vlc-qt-interface.conf 
and change the line beneath [FullScreen] to
pos@Point(320 600)
now ive open a video in fullscreen and just repositioned the control panel to where i want it to stay.

---

### Post by adotei on 2009-04-09
Just as a follow-up to this.

Exit vlc if the application is running before making the above stated changes.

if using a 1280X1024 screen resolution, change the coordinates to (320 960)

---

### Post by Th3Professor on 2009-10-08
Anybody know of the default coords for the controller (control panel) on 1920x1080 res?

EDIT:
And how to make it stick w/ that setting?
I close vlc, I update the config with new coords, and open vlc - the controller is in a new location, then when i either go out of full screen and back again or when i close and reopen vlc and go back to full screen the controller is gone again.

---

### Post by Th3Professor on 2009-10-08
nevermind, it seems to be sticking to the same location, and after some adjusting found a good location on the screen (coords) to put it.

---

