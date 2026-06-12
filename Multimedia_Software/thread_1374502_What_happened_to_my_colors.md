---
title: "What happened to my colors?"
date: 2010-01-06
forum: Multimedia Software
---

### Post by craftypants on 2010-01-06
Awhile ago I installed Avidemux to chop up a video I made of my cat. It was hilarious. But as soon as I installed it whenever I tried to play a video on my computer the colors were all...wrong. 

I'm not really sure how to describe it or even what caused it. If you'll indulge me in a screenshot of what it looks like ([http://www.flickr.com/photos/24569324@N08/4253007206/](http://www.flickr.com/photos/24569324@N08/4253007206/)) I hope that can be helpful. Pretty sure the SG-1 team aren't smurfs...

The only thing I've tried thus far is uninstalling Avidemux. Please let me know what information is needed to help fix this.

Thanks!

---

### Post by 3rdalbum on 2010-01-06
It looks like a symptom of buggy Nvidia drivers.

In your video player's settings (or in the case of Totem, in the gconf-editor settings under Gstreamer) you need to change the "video output module", preferably to X11.

---

### Post by craftypants on 2010-01-06
Problem solved! Thank you!

---

