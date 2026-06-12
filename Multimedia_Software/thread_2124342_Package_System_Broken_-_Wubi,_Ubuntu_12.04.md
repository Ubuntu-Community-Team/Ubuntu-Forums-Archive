---
title: "Package System Broken - Wubi, Ubuntu 12.04"
date: 2013-03-10
forum: Multimedia Software
---

### Post by thenox on 2013-03-10
I was trying to play a DVD w/ movie player and it asked for Gstreamer plugin updates. I clicked to continue, but it came back with the errors in the screen shots. 

So far I haven't dug up anything online. What does this mean?
Screenshots:
[http://i.imgur.com/FzFEGZQ.jpg](http://i.imgur.com/FzFEGZQ.jpg)
[http://i.imgur.com/3cWDPnt.jpg](http://i.imgur.com/3cWDPnt.jpg)

Thank you.

---

### Post by cortman on 2013-03-11
From the terminal run

```
sudo dpkg --configure -a
```

and post back the output.

---

### Post by thenox on 2013-03-11
Thanks, Cortman. I will give that a shot.

---

