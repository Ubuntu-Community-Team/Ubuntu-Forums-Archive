---
title: "RAM for Dedicated Backend Server"
date: 2014-05-22
forum: Mythbuntu
---

### Post by mattlach on 2014-05-22
Hey all,

I apologize if this has already been covered, but I googled the hell out of it, and couldn't come up with any satisfying semi-recent results, so I figured I'd ask.

I'm about to put together my first MythTV setup.  I will be using an ethernet based InfiniTV6.

How much RAM is recommended for a dedicated backend used for 6 HD streams?

The backend will be running on my VMWare ESXi server, so I ahve a lot of flexibility regarding the RAM assignment.  It doesnt need to follow normal stick sizes.   My server shares 32GB of ram between all my VM's, and th eless I use for the MythTV backend, the more I can use for other servers that really need it.   

I wish I could add more RAM, but the free VMWare license limits you to 32GB, and the paid versions cost too much to justify for a home basement server.  I wish they had a lower cost home user license...

Any thoughts appreciated!

--Matt

---

### Post by dannyboy79 on 2014-05-23
4GB should be enough

---

### Post by tgalati4 on 2014-05-23
Switch to Xen.  How much RAM can your server hold?

---

### Post by whosmatt on 2014-05-24
If you upgrade ESXi to the latest version, the RAM limit has been removed.

---

### Post by mattlach on 2014-05-27
> **dannyboy79 said:**
> 4GB should be enough

Thank you.   I will try this first!

> **tgalati4 said:**
> Switch to Xen.  How much RAM can your server hold?

I'm quite happy with VMWare's ESXi / Vsphere, and don't feel like switching right now.  Thanks for the suggestion though.   I will look into it.

I thought it was 64GB, but turns out it's only 32GB, so it wasn't much of a limit for me anyway.

> **whosmatt said:**
> If you upgrade ESXi to the latest version, the RAM limit has been removed.

You know, I had upgraded to 5.5, and not even noticed that the limit was gone!

I got really excited for a brief second until I realized that my motherboard limits me to 32GB (I was convinced I had more than 4 RAM slots...)   At least until unregistered 16GB DDR3 modules become available.

---

