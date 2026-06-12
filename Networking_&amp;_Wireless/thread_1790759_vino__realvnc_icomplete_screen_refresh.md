---
title: "vino / realvnc icomplete screen refresh"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2011-06-25
Hi,
  I am having a problem slightly different from one already addressed here:
 
When connecting to ubuntu 10.04 running vino from another PC by using realvnc (either from an ubuntu box or from windows xp) the screen does not refresh completely. I always get rests from previous windows hanging around. Only when moving a window over the remainig parts of another one that has been closed already, these snippets become erased. I read some posts about this problem arising only in 11.04 but I am having it with 10.04. Suggestions appreciated!
D-E

---

### Post by ZX3Junglist on 2011-09-24
I also have this issue, using intel HDA 3000. Vino leaves messy parts of windows all over the place. Very ugly, and I was hoping for a solution. It looks like an incompatibility between compiz and the way vnc interacts with X, so the only real solution right now is to use another window manager (like metacity) or to force vnc server to do whole-screen refreshes (very slow and/or resource intensive). Anyone have a real solution?

---

