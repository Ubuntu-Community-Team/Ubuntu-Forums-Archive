---
title: "Camera Mic Not Working (USB Audio)"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by osxdude on 2008-04-06
I'm trying to use the mic from my Logitech QuickCam Communicate STX on ubuntu. I have sound prefrences set to "USB audio" however, Sound Recorder returns this error:

Your audio capture settings are invalid. Please correct them in the Multimedia settings.

Now, I cannot go into the Multimedia Systems Selector, as it frezess when I load it up. What the heck am I supposed to do?

(PS: The camera part works fine.)

---

### Post by Matthewslf on 2008-04-07
Try this in terminal and post the output:
```
arecord -f cd -D hw:1,0 ~/test.wav
```
If hw:1,0 doesn't work, try hw:2,0. the first number selects which sound card to use. 0 is the default, 1 is the second, 2 is the third, etc.

---

