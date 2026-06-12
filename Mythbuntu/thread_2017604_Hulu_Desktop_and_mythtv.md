---
title: "Hulu Desktop and mythtv"
date: 2012-07-05
forum: Mythbuntu
---

### Post by w1ll1am on 2012-07-05
Hello I am having an issue with hulu desktop. If I attempt to change the window size hulu desktop crashes. If I click the maximize button or if I try to adjust the window with the cursor I get the same problem. Any ideas?

---

### Post by jdk82 on 2012-07-07
What version of flash are you using? IIRC huludesktop didn't play nice with the open flash solutions last time I was using it, and I had issues with all versions except the newest one. That was a while ago though...

---

### Post by jpaden on 2012-07-07
I've been having the same issue for the last few months.  I still haven't figured out the solution.  I'm on the latest Flash offered by Ubuntu/Mythbuntu 11.10.  I noticed around the same time that Flash in the browser became much less stable.  I'm wondering if Adobe really dorked something up with the plugin.

If you find a solution, please post.  I'm considering trying out Gnash with it (also because Gnash is starting to offer VA-API support), but I'm trying to get my video drivers and VA/XvBA drivers situated and settled in before I start trying to tweak Flash.

---

### Post by w1ll1am on 2012-07-08
> **jpaden said:**
> I've been having the same issue for the last few months.  I still haven't figured out the solution.  I'm on the latest Flash offered by Ubuntu/Mythbuntu 11.10.  I noticed around the same time that Flash in the browser became much less stable.  I'm wondering if Adobe really dorked something up with the plugin.

If you find a solution, please post.  I'm considering trying out Gnash with it (also because Gnash is starting to offer VA-API support), but I'm trying to get my video drivers and VA/XvBA drivers situated and settled in before I start trying to tweak Flash.


```
[display] 
fullscreen = TRUE
width = 1366
height = 768
pos_x = 0 
pos_y = 47

```this worked for me. But now I am having a completely unrelated problem I can't get any sound from flash. I have reinstalled flash and tried gnash.

---

