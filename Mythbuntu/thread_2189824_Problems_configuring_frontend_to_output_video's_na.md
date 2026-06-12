---
title: "Problems configuring frontend to output video's native resolution"
date: 2013-11-24
forum: Mythbuntu
---

### Post by garsh on 2013-11-24
I'd like to configure my Mythbuntu frontend to output recordings at the video's native resolution.  I prefer to let my TV handle scaling & deinterlacing if possible.  I'm mostly worried about HD content, so I'd like to get 1080p (or 1080i if possible) and 720p working.

I've gone to Utilities/Setup -> Setup -> Appearance
On the "Theme/Screen Settings" page:[LIST]
[*]I've unchecked both "Use GUI size for TV playback" and "Use fixed window size".
[/LIST]On the "Video Mode Settings" page:[LIST]
[*]I checked "Separate video modes for GUI and TV playback".
  I've set:  GUI: 1920x1080, Video output: 720x480, Rate: Auto, Aspect: 4:3
[/LIST]Under "Overrides for specific video sizes", I've set:[LIST]
[*]1280, 720, 1280x720, Auto, 16:9
               1920, 1080, 1920x1080, Auto, 16:9
[/LIST]
With these settings, the GUI is output as 1080p, and 1080i recordings are output as 1080p.
Live TV at 720p resolution is displayed correctly at 720p.

**However**, something very strange happens when I try to play 720p recordings.
The signal sent to the TV is 720p.  But what's actually being displayed appears to be the recording, scaled up to 1080p, and then just showing the upper left 1280x720 portion of the full 1920x1080 desktop.  When I bring up the menu, instead of being centered, it's shifted to the right and down, further supporting this description.

Any ideas of how to fix this?

My hardware: [Lenovo Ideacentre Q190]("http://shop.lenovo.com/us/en/desktops/ideacentre/q-series/q190/#techspecs") with [Intel Celeron 887]("http://ark.intel.com/products/69361") and Intel HD Graphics.

---

