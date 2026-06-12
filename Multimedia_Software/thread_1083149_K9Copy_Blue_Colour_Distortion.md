---
title: "K9Copy Blue Colour Distortion"
date: 2009-02-28
forum: Multimedia Software
---

### Post by Cal55 on 2009-02-28
Using K9Copy on 8.10 Intrepid any copied DVDs seem to come out with a blue tone, as though the red is missing from the film.

Anyone have any ideas how I might fix this?

The system I have was upgraded from a working version of Hardy.

Cheers
Cal

---

### Post by Cal55 on 2009-03-01
Bump?

---

### Post by Cal55 on 2009-03-02
I was being a bit dumb here not realising that it was in fact ALL DVD playback, not just archived ones, that appeared blue.

Googling I came across these suggestions: 
[HTML]https://answers.launchpad.net/ubuntu/+source/totem/+question/7373[/HTML]

For my system, to get correct-colour playback I needed in the console to do 
```
gstreamer-properties
```

This started a dialog where under Video/Default Output I changed plugin to the option: 
X Window System (No Xv)

Now back to checking K9Copy

Cheers
Cal

---

