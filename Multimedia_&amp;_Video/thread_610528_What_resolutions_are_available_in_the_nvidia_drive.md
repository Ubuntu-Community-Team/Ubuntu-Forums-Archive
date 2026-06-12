---
title: "What resolutions are available in the nvidia driver for S-Video and Component?"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Levander on 2007-11-12
From the [nvidia driver README](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/chapter-16.html):

> The NVIDIA X driver populates the mode pool for the TV with all the mode sizes that the driver supports with the given TV standard and the TV encoder on the graphics card. These modes are given names that correspond to their resolution; e.g., "800x600".

I've been looking for doc's that say what resolutions are available for the S-Video and Component standards, but can't find it documented.

I have successfully configured S-Video, and from looking at the Screen Resolution utility in Gutsy it looks like 1024x768, 800x600 and 600x480 are available.  They are all listed at 50 Hz refresh, but I don't think that refresh rate listed is accurate - which isn't important for what I'm doing now.

Are those the same refresh rates available for S-Video for other people?  If so, I assume  that's what's the quote above is talking about as "supported" for S-Video.

Then, what resolutions are available for Component?

When I try to configure my TVOut port for Component, I get the same three resolutions that I get in S-Video.  But, the thing is, I know my Component video configuration is wrong.  It's coming out in black and white.

I'm thinking the problem is that when I configure xorg.conf to output the video in COMPONENT, it isn't actually doing that.  Instead, it's outputting the video in S-Video.  And, that's why I'm getting the same resolutions for COMPONENT that I am for S-Video.

In any event, if someone could tell me definitively what resolutions are available for SVIDEO and COMPONENT with the nvidia driver, this would really help out.  Well, tell me definitively, or at least tell me what resolutions are available on their desktop for COMPONENT or SVIDEO.

---

