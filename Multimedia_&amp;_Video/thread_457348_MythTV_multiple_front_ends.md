---
title: "MythTV multiple front ends"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by starfry on 2007-05-28
Hello,

I have two MythTV front ends and they both work nicely. However only one of these can watch live TV at any one time. I find this strange, as other solutions (Nebula's digivt application under windows) are only limited to channels on the same MUX. I think I am right, but thought I'd ask in case...

Can two front ends watch the same live TV stream at the same time?

Thanks!

---

### Post by barney_1 on 2007-05-28
Yes, you can watch the same live-tv channel at the same time on two different boxes.  You cannot, however, watch two different channels unless you have multiple tuners.

---

### Post by starfry on 2007-05-28
Ok, how do I do this then?
When I try, I put frontend A into watching TV. When I try to watch TV on frontend B I get the message that mythtv is already using all available inputs.
Thanks...

---

### Post by barney_1 on 2007-05-29
You just need to enable the viewing of `LiveTV' the listing of recorded programs:

Utilities/Setup --> Setup --> TV Settings --> Playback --> Next --> Next --> Next
```
Show 'LiveTV' recordings when using "All Programs" filter
```

Then when you go to your Media Library --> Recordings you will see the show being watched on another frontend as the top-listed recording.

---

