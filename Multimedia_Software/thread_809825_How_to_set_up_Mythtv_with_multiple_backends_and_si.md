---
title: "How to set up Mythtv with multiple backends and single frontend"
date: 2008-05-27
forum: Multimedia Software
---

### Post by DominicF on 2008-05-27
Hi,

Can anyone advise on setting up Mythtv with multiple backends (running on separate desktop machines - ubuntu) and single frontend (running on a laptop - mythbuntu)?  All running mythtv 0.21.

Basically, I want the easiest way to switch the setup of the frontend so that I can switch between the two backend machine without having to type in the IP Addresses in the setup every time I want to switch to the other machine?

Many thanks,
DominicF

---

### Post by belbo on 2009-07-11
Hi. I have the same question. Interested to know if you ever got a response or found a solution. Please could you let me know ? Would appreciate it. 

Thanks

belbo

---

### Post by bernied on 2009-07-11
I haven't done this but I seem to remember you configure one backend to be the master (should leave this one turned on), then the other backends as slaves. You tell the slaves which is master. When you set up the front end you just give it the master backend.

Then the master backend distributes the work to whatever slave backends are available.

This would all be done through mythtv-setup on the backends.

Does that help?

---

