---
title: "oggz-tools troubleshooting?"
date: 2011-02-22
forum: Multimedia Software
---

### Post by lelandnielsen on 2011-02-22
I'm attempting to cut a video file using oggz-chop in oggz-tools.  I'm using this command:
```
oggz-chop -s 1:00 -e 2:00 video.ogv chopVideo.ogv
```
And receiving in return a screen full of hieroglyphics and terminal stalling.  

I've successfully achieved this before on this computer, but it's been awhile and several updates have occurred.  I have no idea how to troubleshoot.  I'm a bit of a noob, so forgive me if I'm missing something obvious.  Any help is greatly appreciated.  

Thanks in advance.

---

### Post by StephenWoods69 on 2011-05-03
I don't know if you ever got a reply to your question but if you haven't then try this
oggz-chop  -s 1:00 -e 2:00 video.ogv > chopvideo.ogv
It seems if you don't direct the file then it writes the contents to the screen which explains the hieroglyphics on your screen.

---

### Post by lelandnielsen on 2011-05-03
Thanks!  That did it.  So simple.

By the way, in the spirit of "Teach A Man To Fish", where and how do you find this stuff? 
My Googling came up empty on this one.

---

### Post by StephenWoods69 on 2011-05-04
This Wikipedia article explains file redirection which is basically what we just did and also the use of pipes.
[http://en.wikipedia.org/wiki/Redirection_%28computing%29](http://en.wikipedia.org/wiki/Redirection_%28computing%29)
I found this information very useful.

---

### Post by lelandnielsen on 2011-05-05
That is helpful. 
Thanks again!

---

