---
title: "record video from GoogleEarth zoom"
date: 2008-09-14
forum: Multimedia Software
---

### Post by cotcot on 2008-09-14
I want to record the screen when I am zooming in on GoogleEarth from my country to a more detailed point of intrest. 
Is there anybody knowing how to do that ?
First is how to make GoogleEarth zoom slowly and constant between 2 points.
Second is how to record this on a video.

Thanks

---

### Post by skullmunky on 2008-09-16
don't know about the first, but for the second, use "Desktop Recorder" or one of the other methods posted somewhere around here for screen recording.

---

### Post by cotcot on 2008-09-16
For the constant zooming I exercised to do it manually with the googleearth +/- slider. It works fine.

For the capturing I found xvidcap and istanbul.
I could not get a sufficient high framerate with xvidcap. Preferences was set to 10, but i only got 2 or 3. The result was more slideshow than a video. Playing with different file types, settings and window sizes did not help.
Istanbul seemed not giving better result until i tried with 3D enabled. The output is then useful after changing the framerate from 10 (which is obviously the default in istanbul that cannot be changed) to 25. I changed the framerate by rendering the 10 fps clip to a 25 fps clip with blender VSE. The clip time is 2.5 times shorter. After having searched on the net this is not easy to do. So I was very surprised that blender VSE did it right from my first attempt correctly.

---

