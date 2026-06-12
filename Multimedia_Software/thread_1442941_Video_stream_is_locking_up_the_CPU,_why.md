---
title: "Video stream is locking up the CPU, why?"
date: 2010-03-30
forum: Multimedia Software
---

### Post by johnuk on 2010-03-30
Videos keep freezing, then going, then freezing, even if I've just reset and have nothing else running. I've tried increasing the cache to 20s.

Examining system monitor during these freeze ups, I noticed the following;

[IMG]http://i44.tinypic.com/rvxe29.png[/IMG]

First of all, the CPU is running hard to decode the stream it seems. But then, without me touching anything, it periodically hiccups and jumps to 100%, freezing the video.

What's more strange, is with the video paused, I get the following;

[IMG]http://i44.tinypic.com/fe1g2g.png[/IMG]

The codec shouldn't be taxing the CPU if it's paused I'd have thought, but check it out.... it's still running the CPU near it's limits. If I close the player, note the massive drop off in CPU usage.

I've heard that using DirectX will dump some of the processor usage onto the video cards processor, but will that work if I install the windows version and run it through wine?

And why's the CPU still being utilised so much and hiccuping when it's not decoding?

Thanks for reading! John

---

