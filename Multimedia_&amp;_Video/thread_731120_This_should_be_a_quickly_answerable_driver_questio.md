---
title: "This should be a quickly answerable driver question"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by xela321 on 2008-03-21
I just wanted to verify the behavior I'm getting on my machine.  I have the newest ATI binary driver (for my radeon hd 2400) and fglrxinfo looks correct.  glxinfo also shows direct rendering.  And, I have the Composite extension section of my Xorg.conf commented out as recommended here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Here is the behavior I want to verify:

When I run glxgears, one of my CPU cores shoots to 100% usage.  I was under the impression that all of that would be done on the GPU in the video card.  Am I right, or is glxgears really supposed to operate this way?

Second, when I'm using Compiz I get two more odd behaviors: One, video playback is choppy. Second, when I rotate the cube or drag a wobbly window around, the X process increases its CPU usage.  Is this also normal?

---

