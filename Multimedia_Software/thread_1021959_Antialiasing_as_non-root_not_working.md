---
title: "Antialiasing as non-root not working"
date: 2008-12-26
forum: Multimedia Software
---

### Post by lays on 2008-12-26
Hey there,

recently updated my kernel to 2.6.28 and so I had to do with the NVIDIA drivers. On my previous kernel I was using 100.14.19 and the problem didn't exist but those won't run on such a new kernel so I'm stuck with 177.80, 177.82 and 180.18 but on all of these I have the same issue. Antialiasing won't just work in applications run as a normal user, e.g. sudo glxgears will give me a nice smooth picture but ran normally the edges would be all spiky and ugly. So my guess is that it's a problem with file permissions if it works from root. I also guess I should use strace to track the problem but in fact, strace what? glxgears? Or nvidia-settings?

Or maybe any other way perhaps?

---

