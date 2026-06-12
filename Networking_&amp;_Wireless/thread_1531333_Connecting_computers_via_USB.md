---
title: "Connecting computers via USB"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by dean.s.wood on 2010-07-14
Hi,

I have an interesting question (well for me anyway). I have 2 i7's sitting on my desk. I can't connect them via network ports because they are in use. I would quite like to connect them to have a mini cluster (very mini but still 16 cores could be useful). It would also be nice for them to have a fairly high speed interconnect, would speed up my code. It seems to me USB is almost perfect, except you can't just plug 2 usb ports together as that is a recipe for a fried motherboard. 

However, I have seen certain USB cables with a chip in the middle to stop this happening and was wondering if anyone has any experience getting these things working on Ubuntu? Even if I did have network ports available, going via USB is desirable as I know USB 2 has a higher rate than most standard ethernet connections. I would ideally want it to work as a mini-network so I could use MPI in my code to get parallel processing going on.

If anyone has any ideas, that would be awesome and I apologise for the length of this post.

Thanks

Dean

---

### Post by dmizer on 2010-07-15
You won't get very high I/O via USB. Is there some reason you can't use the LAN as your communication point for the cluster? I mean, just because you are also using the LAN for access to the internet doesn't mean you can't also use it for cluster traffic.

If I recall correctly, it's rediculously easy to set up a beowulf cluster with [Knoppix](www.knoppix.net). There are a bunch of live CD's that are designed for this purpose, I suggest you take a look around.

---

