---
title: "How to shut down esd sound device?"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by hajk on 2006-07-14
I'm experiencing some problems that appear to be related to the esd sound daemon (?) -- is it possible to shut this off? I used to have no problems using alsa/oss, so I want to try and do sound the old-fashioned way again.

Any help appreciated.

---

### Post by Paerez on 2006-07-14
I know you can do a one-time shut-off by typing:
```
# killall esd
```
but I don't know how to make it permanent (it will come back after logging in again I think. definitely after a reboot).

---

