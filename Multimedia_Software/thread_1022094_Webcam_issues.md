---
title: "Webcam issues"
date: 2008-12-26
forum: Multimedia Software
---

### Post by LegoAddict on 2008-12-26
I am running a Dell Inspiron 1525 with an Intel TI800 2.1 ghz processor, 4 gigs of RAM, Ubuntu Intrepid 64 bit and Windows Vista 32 bit, and using the built-in video camera from the Windows edition of the 1525 (long story).


So I've had moderate success with my webcam.  Windows, no surprise, sees it perfectly.  After a little convincing, Skype for Linux sees it fine too.  However, neither Cheese nor Camorama like it.  Camorama returns:

Could not connect to video device (/dev/video0).  Please check connection.

Cheese opens but does not display an image, then crashes as soon as I touch the effects.

Now, Skype is calling it video1.  Cheese wouldn't open until I turned video0 in /dev to a symlink to video1.  Now it opens and crashes instead of effects.  However, Camorama doesn't recognize this.

If there's anything I can do to give more info, just say the word.  I would like to be able to use Cheese the most, but if Camorama works that's fine too.

---

