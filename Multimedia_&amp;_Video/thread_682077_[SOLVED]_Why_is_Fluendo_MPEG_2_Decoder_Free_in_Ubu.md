---
title: "[SOLVED] Why is Fluendo MPEG 2 Decoder Free in Ubuntu When it Costs 7 Euros?"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by user2037 on 2008-01-29
Fluendo offers their MP3 Decoder for free. However, their MPEG 2 Decoder costs 7 Euros:
[https://shop.fluendo.com/product_info.php?products_id=48](https://shop.fluendo.com/product_info.php?products_id=48)

So why does the decoder appear at no cost in the Ubuntu software sources at [http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-fluendo-mpegdemux](http://packages.ubuntu.com/gutsy/libs/gstreamer0.10-fluendo-mpegdemux)

Shouldn't this be in the "non-free" repo or excluded entirely?

---

### Post by disturbed1 on 2008-01-29
They aren't the same. One demuxes (split video/audio/subpicture/navpacks from the container) the mpeg stream, the other (not free one) decodes the video.

---

