---
title: "Color problems"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by impleri on 2007-02-04
Hi.  I am setting up a box for a MythTV install and have run into one big problem: color.  I have an nvidia video card with TV-out (S-video and Component).  I am using the component out to my TV and have TwinView configured properly.  X is outputting to both screens, but the TV output is way off color.  I have played with nvidia-settings and nothing has made it bearable.  It seems like the TV out is not sending any information for the blue channel, so everything comes out in a purple-ish, low saturation view.  Has anyone else had this problem before?

---

### Post by impleri on 2007-02-04
Figured it out, thanks to searching nvnews.  The TVOutFormat should be "HD480i" not "NTSC-M" for component out.

---

