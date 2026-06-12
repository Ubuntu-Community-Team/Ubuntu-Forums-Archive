---
title: "nvclock/smartdimmer segfault on new nvidia drivers"
date: 2012-05-02
forum: Multimedia Software
---

### Post by lastguru on 2012-05-02
I have used nvidia proprietary drivers (downloaded from nvidia.com, not the ones packaged with ubuntu) on my Sony Vaio Z-series notebook with ubuntu 11.10 for a while and they worked fine. After recent upgrade from 290.10 to 295.40 (also tried the latest beta 302.07) the display brightness do not change. Everything else works, but brightness control.

All hardware buttons work as expected (I can see notification of events) - it is an nvclock and smartdimmer problem. They return segmentation fault on any action:

```

$ nvclock -i
Segmentation fault

$ smartdimmer -g
Segmentation fault

```

I can downgrade to 290.10 and all works fine again.

Any ideas how to fix this?

---

### Post by paulatz on 2012-05-19
Someone opened a bug report for it 2 weeks ago on the Debian tracker, one week ago I've also provided the information which should be necessary to fix it but nobody seems to have cared since

I hope the situation will improve since, maybe you can vote in the issue to try to have it checked.

---

