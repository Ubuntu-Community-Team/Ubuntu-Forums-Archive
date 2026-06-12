---
title: "Via sound problem"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by gordon3913 on 2007-03-02
My computer was getting this message in kubuntu and now in ubuntu:-
"sound server fatal error - cpu overload, aborting" and the system would momentarily freeze.

After a bit of checking I added "snd-via82xx" to the /etc/modules file.

This still did not work. I have now added "snd-via82xx dxs_support=5" to the /etc/modules file.

This now appears to work.

:)

---

