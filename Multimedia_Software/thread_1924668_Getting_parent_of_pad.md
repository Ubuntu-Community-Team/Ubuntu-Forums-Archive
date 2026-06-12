---
title: "Getting parent of pad"
date: 2012-02-13
forum: Multimedia Software
---

### Post by Goutham S on 2012-02-13
I am new to gstreamer and saw this code in the chain function chapter in the Plugin Writer's Guide.

GstMyFilter *filter = GST_MY_FILTER (gst_pad_get_parent (pad));

The push function is called as follows.

return gst_pad_push (filter->srcpad, outbuf);

Is it absolutely necessary to pass the pad as filter->srcpad when the chain is already called in the srcpad. Or can I just pass the pad argument of the chain function?

In other words, is getting the parent of the pad necessary if I don't use it explicitly? This is maybe a naive question but I wanted to get my doubt cleared. Also point me where I should ask this question if this is the wrong forum.

Thanks.

---

