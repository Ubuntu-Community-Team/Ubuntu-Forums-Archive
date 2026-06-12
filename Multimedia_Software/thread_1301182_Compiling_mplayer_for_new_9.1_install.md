---
title: "Compiling mplayer for new 9.1 install"
date: 2009-10-25
forum: Multimedia Software
---

### Post by mcgeek on 2009-10-25
I have just installed kk on a Asus 1000HE. Other than running update manager it is clean. Now that all (I hope) issues with the intel chipset and video have been cleared up I want to get as much from mplayer as I can.

This isn't a question on how to compile mplayer (I have done that several times) what should I compile as far a codecs and libs to make mplayer as fast a possible. Is there any way to compile for the atom processor? Is it all a waste of time? Should I just go with Synaptic and make it easier on myself?

Thanks

---

### Post by andrew.46 on 2009-10-26
Hi mcgeek,

If it is only a question of speed I believe there is a small lag with the repository offering which will use the *--enable-runtime-cpudetection* that will not be present with a self-compiled copy; and perhaps even this will not be noticeable if your system is fast enough. But the Karmic MPlayer is pretty capable and you may very well find the slight startup lag compensated by the fact that the pain of compiling is not present :).

All the best,

Andrew

---

