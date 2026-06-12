---
title: "Video has color issues after upgrade from 9.04 -&gt; 9.10"
date: 2009-10-29
forum: Multimedia Software
---

### Post by shaggy999 on 2009-10-29
I just encountered some really weird problems. I upgraded from 9.04 -> 9.10 which went off without a hitch. I had a flash video file I nabbed from youtube on my computer that I watched yesterday just fine. I decided to watch it again and when it opened all of the colors were distorted like when you play with the color values on a TV and make it so peoples faces are purple and the sky is hot pink.

I thought that was weird and loaded the video up with vlc instead of the default movie player and had the same problem. So I decided to go back to youtube and see if it was distorted in the browser. It was NOT distorted, everything played fine. So I re-downloaded the video and tried watching the video again in VLC and default movie player. Distorted colors still.

Next I popped in a divx-encoded movie and it also had the distorted colors. I then tried to see if I could change video settings in the default video player but it seemed to be light on configuration options.

Checking VLC I changed the video output from 'default' to 'X11'. Suddenly the video plays just fine. Default video player still does not.

Anybody have an idea on how to fix this issue with the default video player (Totem movie player)?

I have:

Karmic 64-bit
Latest nVidia drivers for nVidia Geforce 8800 GTX

---

### Post by shaggy999 on 2009-10-29
Ok, that's weird. I just went back into the video player's settings and noticed the "hue" bar was completely to one end whereas all the other bar settings were in the middle. I clicked "set to defaults" and it put the hue setting in the middle. Everything works fine now. How odd.

---

### Post by tgilbert328 on 2009-10-29
I had the exact same problem.  Thanks for recommending I check the obvious because I probably would have spent the rest of the night checking everything else.

Tim

---

### Post by Marogian on 2009-10-30
Same problem with me- hue was set right to the far left after upgrading to 9.10.

Thanks for identifying the problem!

---

### Post by VastOne on 2009-10-30
I recall this same issue in other major upgrades. Glad you were able to get it solved so quickly.

---

### Post by DesertBlade on 2009-10-30
Much better. Thanks!

---

### Post by ChaoticMind on 2009-10-31
For me, the Hue bar is set in the middle already, and the colors are messed up as the original poster said. Setting it either to the extreme right or extreme left fixes the problem however, weirdly enough. Clicking "reset to default" puts the hue bar in the middle, and reverts to skewed colors. 

I'm just gonna put it to the far left (or right).

---

### Post by bladz01 on 2009-11-07
LOL what an easy fix.  I've dealt with that issue so many times.  Thanks for the easy fix.

---

