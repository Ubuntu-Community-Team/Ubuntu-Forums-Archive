---
title: "VIDEO FREEZES SCREEN and I have an Intel Video Card!?"
date: 2008-09-26
forum: Multimedia Software
---

### Post by camputer on 2008-09-26
Well, I have posted before with no comments. Here goes round 2. 

I have a Intel GMA x4500 video card in my Lenovo SL 400 laptop. Compiz effects work fine, adobe flash videos work fine (online streaming). ALL OTHER VIDEO including .avi, .mpg, .wmv all FREEZE the screen :(.

I can't figure anything out. I dont have the fancy Intel GMA X4500HD or anything. Just the GMA x4500 (its a pretty new release from Intel though). 

Any help at all is appreciated!!!

---

### Post by camputer on 2008-09-26
Please someone help... anyone

---

### Post by camputer on 2008-09-27
Anyone know where to start? I tried turning off compiz with no luck...

---

### Post by ENigma885 on 2008-09-27
it can be ur video player, ur video output or both..
so 
- try SMPlayer , as the names suggests it's based on MPlayer,
```
 sudo apt-get install smplayer
```

- once it's installed from the *Options menu >> Preferences >> General "left" >> Output Drivers*
choose _**X11**_ as video and _**PulseAudio**_ as audio 
then Apply and OK

---

### Post by camputer on 2008-09-27
THANKS! It works! I think! I still have yet to try other things than AVI but it totally has worked so far! You are so awesome!

---

