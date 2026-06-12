---
title: "Hardy Heron cheese is slow. How do I set it to use xvimagesink?"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Coward on 2008-05-11
Cheese is slow now that I've upgraded to Ubuntu Hardy Heron from Gutsy Gibbon. I've done a lot of searching and found this message:

"ATTENTION: If you are getting a really slow response with the video, the video is sluggish and everything looks quite slow, like as the video lags, you may have set "ximagesink" (X Window System (No Xv)) as video-output. This means, that your cpu is doing all the work. Change it to "xvimagesink" (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work." -at ([http://linux.softpedia.com/get/Multimedia/Graphics/Cheese-28762.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/Cheese-28762.shtml))

It seems like this might be the problem, but I am not a linux expert, so I'm not sure how to do this. Where is the option to change it to "xvimagesink".

Never mind changing the property, found it in the help (run "gstreamer-properties"). Then I rebooted and Cheese is still slow so this doesn't solve the problem.

---

