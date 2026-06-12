---
title: "Overlaying image onto GIF animation is aligned improperly"
date: 2011-05-16
forum: Multimedia Software
---

### Post by meridionaljet on 2011-05-16
Hello,

I'm on Ubuntu 11.04, and am trying to overlay a static blue coastline image onto a geostationary animation with 12 frames using imagemagick. I have received no replies from them on their forums.

The code I used to create the composite animation is as follows:

```
convert \( animation.gif -coalesce \) null: \( outline.tif outline.tif outline.tif outline.tif outline.tif outline.tif outline.tif outline.tif outline.tif outline.tif outline.tif outline.tif -coalesce \) -layers Composite composite_animation.gif
```

The resulting animation is below:

[IMG]http://oi56.tinypic.com/2w23msk.jpg[/IMG]

It's a bit hard to see, but the blue outline should be aligned much farther to the left on the image, but the vast majority of it is cut-off to the right because it is shifted so far. It should be centered. Both the outline and the background are actually cropped regions out of respectively larger images that are identical in size and are designed to be overlaid. If I choose a cropped region farther to the right on the background animation, the cropped blue outline of the same region won't even show up at all after the overlaying, as if it is shifted completely off the screen for some reason.

I have had success overlaying outlines before with the above command, but here it is not working. I tried appending "-gravity center" to the command with no success. If anyone can help, it would be appreciated.

---

