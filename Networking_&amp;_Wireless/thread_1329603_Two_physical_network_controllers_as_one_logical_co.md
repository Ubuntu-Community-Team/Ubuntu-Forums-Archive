---
title: "Two physical network controllers as one logical controller"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by amentajo on 2009-11-17
I've looked high and low for this one, and I have failed to find a solution that fits my needs, or claims to fit my needs without confusing the heck out of me.

First, my specific situation: I am living alone in a campus dorm room built for two people.  Therefore, I have access to two wired connections, each of which can run at ~10 Mb/s (~1.25 MB/s) download.  I also have a desktop computer (currently running Jaunty) that has two configured network controllers (eth0 and eth1).  One connection is directly fed into the campus network, and the other goes through a personal router connected to the campus network.  Each of these connections individually can ping remote servers successfully.  In theory, then, the only thing standing in the way of me being able to "double my bandwidth" is software.

Can someone can help me find a way to use the two physical devices (eth0 and eth1) as one load-balanced logical device, analogous to a RAID 0 setup with disk drives?  It is theoretically possible for a program that manages multiple connections (e.g., deluge, pan, aria2) to achieve double speeds with this setup.

What I'm specifically trying to do, in short, is find a solution that creates a logical network controller that routes new connections to either of two physical network controllers, determined by whichever is currently the "most idle", i.e., whichever one's current download rate is closest to zero.

---

### Post by greenstar on 2009-11-19
I'm subscribing to this thread because I'm also interested in this question, so let me pull up a chair and hang out. 

I hope someone knows something about this, as I've asked myself this same question before. Problem is, I don't know the answer.;)

It would be awesome if this is possible.

Greenstar

---

