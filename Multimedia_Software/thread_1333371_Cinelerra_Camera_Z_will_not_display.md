---
title: "Cinelerra: Camera Z will not display"
date: 2009-11-21
forum: Multimedia Software
---

### Post by beccatoria on 2009-11-21
Hi all, 

First, full disclosure, I'm a linux newbie, but I'm very open to following instructions and learning more and, you know, trying stuff.  So far I'm loving using Ubuntu - my laptop runs cooler, faster and is generally more awesome.  Similarly, Cinelerra, while it has a bit of a learning curve, is a fantastic piece of software that I'm thoroughly enjoying.  I installed it per the instructions on the Cinelerra CV website and the install went smoothly.  

That said, I have a really weird issue.  I love that I can pan horizontally and vertically using the histograms on the timeline (Cameras X and Y), but the blue histogram - Camera Z - doesn't show up for me whether it's checked under the view menu or not.  (Neither does Projector Z).  

I can still zoom by shift-dragging in the compositor, but this is nowhere near as intuitive and easy as the histogram method since the level of zoom doesn't reset at the start of each clip.  

Once, for no reason I can possibly name, Camera Z did show up, and there was much rejoicing, but the next time I opened up the program it was back to its invisible state and nothing I try seems to make it show up and I can't think for the life of me what I did to make it show up that once.  I don't think I did anything out of the ordinary.  

I've had a look around and can't find anyone else reporting this issue, which makes me wonder if I'm missing something extremely obvious?  

Any help would be appreciated.  

I'm running Karmic Koala (not the netbook remix, even though I have a laptop) and it's 64 bit.

---

### Post by mcp3105 on 2010-07-22
This may be caused by the wrong setting of the value range to be displayed in the Track.
Go to the bottom line of the main window.
There's a selection button in the center of the bottom line, that is by default set to "Audio Fade:". Set it to "Zoom:".  The numbers on the right side of the button probably read "0.000 to 0.000" in your case. Change that to "0.5 to 2.0" and watch the blue line appear.

---

### Post by vace117 on 2010-08-17
deleting message...

---

