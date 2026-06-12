---
title: "How many nodes are my packets passing through?"
date: 2010-11-29
forum: Mythbuntu
---

### Post by rbeer on 2010-11-29
There's nothing technically wrong with my set-up but I'm interested if anyone with networking knowledge could see any future problems with my arrangement.

I have a wireless router with a NAS attached and connected to a switch upstairs which my backend is connected to. All MythTV recordings are stored on the NAS. 

As far as I see when I watch a recording on one of my frontends wirelessly the request must pass:

Frontend --> WiFi Router --> Switch --> MythTV Backend

then the backend must access the recording:

Backend --> Switch --> Router --> Nas

and then the recording must go to the backend, and then reverse again going back to the frontend.

This starts to hurt my head and seems like there are lots of things going on simultaneously. Should I be worried about anything i.e. adding additional frontends? or is the IP protocol and consumer grade kit have sufficient for what seems to me an excessively long route?

---

### Post by CharlesA on 2010-11-29
That's a really short route.

As long as you have a fast network, you'll be fine.

---

### Post by ian dobson on 2010-11-29
Hi,

Your average web browing session goes much further than this, maybe 5-9 hops from your pc to the web server.

Even my local network has 3 hops (frontend to router, gigabit connection to backend switch, switch to Backend server).

The only thing I can see is that the switch is being hit hard by the communiction from the backend to the nas and from the backend to the frontend. But that's the idea behind a switch, it switches between ports so that several devices can send/receive at the same time.

Regards
Ian Dobson

---

