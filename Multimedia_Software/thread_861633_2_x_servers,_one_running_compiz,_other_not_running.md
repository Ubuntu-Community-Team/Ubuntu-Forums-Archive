---
title: "2 x servers, one running compiz, other not running compiz"
date: 2008-07-16
forum: Multimedia Software
---

### Post by han555 on 2008-07-16
Hi, I currently have 2 X servers running.  One for my main desktop and one for my projector for movies.  If I enable compiz, it is enabled on both servers and runs very slow.  What I would like to do is just run compiz on my main desktop and not run it on the x server for my projector.  Can anybody help me out?

---

### Post by tgrimley on 2008-07-16
I don't know too much but if you have an nvidia card you can try going back to one X server and use twinview... just a thought.

---

### Post by han555 on 2008-07-16
I can't use twinview because they two monitors have different resolutions

---

### Post by tgrimley on 2008-07-16
maybe it's not called twinview but I'm using the nvidia control panel with two monitors at different resolutions...

---

### Post by han555 on 2008-07-16
the only options I have are for twinview and seperate x screens.  if it uses twinview the second montitor is a clone of the first and, since the first has a larger resolution, the second has to pan.  this is no good for movies... or much of anything as far as I can tell :)

---

### Post by tgrimley on 2008-07-17
I'm confused.. what version are you using?

[[IMG]http://img186.imageshack.us/img186/1194/screenshotnvidiaxserverlt0.th.png[/IMG]](http://img186.imageshack.us/my.php?image=screenshotnvidiaxserverlt0.png)

I'm using 169.12 drivers and 1.14 for nv control panel

---

### Post by Jean__ on 2008-07-17
I have my monitor and tv as 2 separate x screens.
The compiz settings applet has an option at the left top in the window to choose a screen in my case, screen 0 or screen 1, so for each I can define if I want the cube etc.
Maybe this helps.

---

### Post by han555 on 2008-07-17
i have the same driver and software versions.  you don't have ANY panning when you move your mouse to the edges of your second monitor?

---

### Post by han555 on 2008-07-17
jean, i do not want to run compiz at all.  just disabling different effects would still leave compiz running though.

---

### Post by Jean__ on 2008-07-18
Yes I think so.
You could try starting a terminal on your second and typing kwin --replace but I'm just guessing here, didn't try that myself.

> **han555 said:**
> jean, i do not want to run compiz at all.  just disabling different effects would still leave compiz running though.

---

### Post by han555 on 2008-08-10
I still have not figured this one out.  Tried replacing compiz with metacity on the second x server (metacity --display=:0:1 --replace) but it winds up resetting my primary x server too.  Ideally I'd just like to prevent it from loading at all anyway.  Isn't there a config file where I can specify which to use for each x server?

---

