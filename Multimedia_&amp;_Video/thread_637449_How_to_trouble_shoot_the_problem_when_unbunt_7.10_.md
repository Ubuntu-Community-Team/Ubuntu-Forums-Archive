---
title: "How to trouble shoot the problem when unbunt 7.10 logs me out ?"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-12-11
Hi,

I am trying to setup myth-tv 0.20.2 on ubuntu 7.10. 
When i start to 'watch live tv', ubuntu 7.10 logs me out automatically. 
I assume it crashes or something like that.

How can I trouble shot my problem? Where can I get the log of what causes the crash?

Thank you.

---

### Post by DominicF on 2008-02-19
Hi,

I was getting the same problem, in my case it was to do with my  graphics card (nvidia 8400gs) not supporting XVMC.  The soultion I had found was to start up a terminal window and type:

export NO_XV=1

Then startup mythfrontend by typing:

mythfrontend

This helped me.

---

