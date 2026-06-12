---
title: "New Webcam! help please!"
date: 2008-12-25
forum: Multimedia Software
---

### Post by %hMa@?b&lt;C on 2008-12-25
Hi, I just got a new webcam for christmas, an HP EW193AA and am having a lot of trouble setting it up.  lusb gives this
```
Bus 002 Device 003: ID 093a:2621 Pixart Imaging, Inc.
```
cheese leaves me with nothing. as does skype.  anything to point me in the proper direction would be great.  No need to hold back, I'm familiar with the command line and have used linux for years.  I'm on intrepid x86_64

update: Ekiga displays the webcam but at ~2 FPS instead of the 30 that it can do.  :(  still nothing else ( i need skype) is helping

---

### Post by %hMa@?b&lt;C on 2008-12-26
bump.  more info.
cat /dev/video0 gives some output when i put my hand closer/further from the camera.  if i run
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so '/home/crowell/Desktop/skype_static-2.0.0.72/skype' 

i get it to work, but _only_ then, i have to load the 32 bit version of vid4lin.  I also dont get any sound then.  which sucks :(

---

