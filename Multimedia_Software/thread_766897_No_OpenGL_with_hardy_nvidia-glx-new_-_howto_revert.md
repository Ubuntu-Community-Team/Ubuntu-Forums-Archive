---
title: "No OpenGL with hardy nvidia-glx-new - howto revert back to gutsy drivers?"
date: 2008-04-25
forum: Multimedia Software
---

### Post by inkaine on 2008-04-25
Hey,

after upgrading my cup of Kubuntu from Gutsy to Hardy I'm no longer able to run any OpenGL application. I finally found out why - nvidia stopped support for non-SSE-CPUs like my good ol' Athlon. So the last working drivers for me would be those from gutsy (ver. 100.14.19). However they are compiled against the 2.6.22 kernel, so I can't use them in Hardy right away, am I correct?

So, how can I get the nvidia-glx-new driver from gutsy to work in hardy? Is there a way to forthport (in contrast to backport) with prevu? Or can I just download the source package and compile? I would prefer not to use the binary driver from the nvidia site but if that's my only choice I'd take even this.

Any help would be appreciated, how to get me going on openGL again. Thanks in advance.

---

