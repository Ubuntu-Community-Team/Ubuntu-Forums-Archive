---
title: "Mythgallery and frontend crashes"
date: 2012-07-10
forum: Mythbuntu
---

### Post by jim09 on 2012-07-10
I notice that I am getting front end crashes when using the Mythgallery slide show feature and the transition is set to one of the following:
circle out
multi circle out
blobs
random
I think random is the default.  Setting to one of the other options seems to be fine.  Meltdown only works the first time and noise seems to have no effect.  It seems consistent on 2 machines, 1 FE and a FE/BE combo. FE crash code 139.  They are both fresh installs of 12.04.

kern.log ...
Jul 10 10:53:39 jim-mythbuntu-remote kernel: [  390.389458] mythfrontend.re[1486]: segfault at 28 ip b5c11f24 sp bfbe1490 error 4 in libQtGui.so.4.8.1[b58d6000+aaa000]
Jul 10 10:54:23 jim-mythbuntu-remote kernel: [  434.677771] mythfrontend.re[1953]: segfault at 28 ip b5b94f24 sp bfe6e000 error 4 in libQtGui.so.4.8.1[b5859000+aaa000]
-----------------------------------------------------------------------------

---

