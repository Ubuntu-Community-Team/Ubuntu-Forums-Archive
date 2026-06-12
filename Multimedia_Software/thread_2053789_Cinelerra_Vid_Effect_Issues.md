---
title: "Cinelerra Vid Effect Issues"
date: 2012-09-06
forum: Multimedia Software
---

### Post by pete0403 on 2012-09-06
I'm desparate for a solution here!
 
I have a video sequence that I'm editing to look dream-like and adding music. The way I'm trying to do this is having two of the same clip on different video tracks, the bottom clip has blur and brightness effects on it, the upper clip is set to "addition" with transparency at 50%.
 
My problem is that I can make the bottom clip fine but as soon as I try to add the top clip, the bottom clip eventually gets all weird and streaky at the top of the frame (about half way up it's just streaks and blocks). I've tried this about every conceivable way (rendering bottom clip then adding top clip, rendering everything together, rendering one effect at a time, etc). The anomaly starts at different times each render but always somewhere in the middle of the clip until the end.
 
Can anyone help me with this? Please let me know if you want additional details or a short example clip. I've de-interlaced the base video clip which is rawDV and am rendering to Quicktime for Linuxif that helps. I don't have much hair left and I can't afford to pull anymore out!

---

### Post by pete0403 on 2012-09-08
So I remade the video adding all the effects and this time rendered it to raw DV (same as input file.  I did not de-interlace the video as is suggested when adding a blur effect and this time it worked fine.  I'm not sure whether it was the raw DV to Quicktime for Linux conversion or the deinterlacing that was causing the issue.

---

