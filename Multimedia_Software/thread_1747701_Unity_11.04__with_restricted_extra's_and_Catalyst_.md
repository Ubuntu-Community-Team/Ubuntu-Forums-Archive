---
title: "Unity 11.04  with restricted extra's and Catalyst ATI driver"
date: 2011-05-02
forum: Multimedia Software
---

### Post by Richard Carlson on 2011-05-02
Firefox 4.01 videos are crappy and break up on the screen. I installed Ubuntu ATI catalyst driver for my video card and the Ubuntu restricted extra's (flash) etc. and now video's on Firefox are all messed up and don't work properly. They are all broken up and seem not to load properly. Any idea's? The video's on 10.10 worked great with the above driver's and restricted software. 


Richard:confused:

---

### Post by johnnyredshirt on 2011-05-02
Same problem here. Flash vids suck. Have ati hd3200, athlon neo x2 L335 with restricted driver installed on 11.04.

---

### Post by Richard Carlson on 2011-05-02
Just another note. . . . Chromium works fine for video's. I just yank Firefox altogether.  

Maybe it had something to do being Firefox 4.01? Dunno. . . .

Rich:confused:

---

### Post by handy on 2011-05-03
You'll likely get better video via the original FOSS Gallium driver stack. The 3D isn't as good as Catalyst yet though.

---

### Post by Yellow Pasque on 2011-05-03
Remove the Ubuntu version of Flash and use sevenmachines' PPA:
```
sudo apt-add-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer
```

---

### Post by handy on 2011-05-04
Perhaps the currently being distributed via Canonical & the net bug fix, will solve this problem?

---

