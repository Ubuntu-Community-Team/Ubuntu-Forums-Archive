---
title: "Media Ripper"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by 3guk on 2008-04-07
Ok,

Here is a complex one for you guys, I'm still working with Linux, I have been a user for around 2 years but would hardly say I am a power user.

My mum and dad are predominantly mac users, and I'm looking to set them up with a simple linux filesever on their home network, now I have this set up with Samba, the next problem I have is music sharing. I have looked at a few different ways client side, but there does not seem to be an easy way to do this, especially given neither of them are technical and I live the best part of 300 miles away.

So my second idea was server side, using mt-daapd to create a shared library that all of the iTunes computers can see, in theory this idea should work really well, as they both would like access to their music librarys at different times.

They have around 600CDS and the majority of them are unripped, I'd like to add to the filesever such that they insert a CD into the server, it rips it at 192kbps and saves it to a folder accessible through samba. mt-daapd then checks this directory every few minutes and appends the itunes share as and when.

I can't find a way of automating this process, I have mt-daapd automated perfectly, but it is the CD ripping that I struggle with, there is nothing afaik that will rip the CD and then eject it. The linux box runs as a headless server, so ideally it needs no user interaction !!

Anyone got any ideas on how to achieve this, I have their server for a week at my place to try and come up with a decent solution.

---

