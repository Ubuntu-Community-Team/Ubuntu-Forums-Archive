---
title: "[SOLVED] mythtv &amp;amp; Hauppauge 500 blank screen"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by a_posse_ad_esse on 2007-08-16
I recently purchased a Hauppauge 500, and am able to get video this way:
```

cat /dev/video0 > /tmp/test.mpg
mplayer /tmp/text.mpg

```

Mythtv only shows a blank screen when trying to view TV and does not record.  

I am thinking that the card is configured properly, as I am able to get video in the way described above.  Is this a myth settings issue?

---

### Post by a_posse_ad_esse on 2007-08-17
The MPEG-2 encoder setting needs to be enabled in order for the cards to work properly.

---

