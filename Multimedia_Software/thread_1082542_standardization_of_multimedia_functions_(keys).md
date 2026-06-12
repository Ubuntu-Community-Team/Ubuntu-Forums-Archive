---
title: "standardization of multimedia functions (keys?)"
date: 2009-02-27
forum: Multimedia Software
---

### Post by kcrouse on 2009-02-27
Hello all,

I'm trying to plug-in to the non-mostly-standardized protocol that multimedia keyboards are using.  I can explain the why if you are interested, but here's the short of it - 

You have a keyboard with multimedia keys (like 'next').  You hit it, it emits the hardware keycode (ex. 171), which the X server (or possibly the kernel?) interprets (for gnome on an hp tx100z, this would be XF86AudioNext).  That's all dandy.  Now the XF86AudioNext event signals *something* that most reasonable media programs will interpret as a signal to go to the next song.  

What is that *something*?
What is the protocol for it and how can I learn more about it?

The shortest I can say is I am making a simple remote sever for these functions so that I (and my roommates) can use different music players and still have basic player controls through a single remote interface (think media/tv box and us with out laptops and/or cell phones elsewhere in the apartment).  We can't just signal keycode to X11 because if you remote in (ssh -X) to start the server, and then connect to it, the keycodes will be executed on the client computer and not the one that you've logged into !  So we can't just simulate keypresses but need to link into the system that the X-server is signalling with the keypresses.

K

---

