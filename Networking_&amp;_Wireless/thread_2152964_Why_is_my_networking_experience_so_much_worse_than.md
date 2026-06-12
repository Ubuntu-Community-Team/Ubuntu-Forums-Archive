---
title: "Why is my networking experience so much worse than on Windows?"
date: 2013-06-09
forum: Networking &amp; Wireless
---

### Post by StephanG on 2013-06-09
Hi Guys,

I currently have a Kubuntu machine set up as a home server, using Samba.  It has three partitions mounted to three folders that are shared over the network.  When I access those folders from a Windows 7 machine, I get the full 100 Mbit network copy speed, and if I mount the folder as a drive on the Windows machine, I can even see how full the partition is.

But, when I access the shared folder from my Kubuntu installation, I haven't found a way of seeing how full the partition is, despite the fact that the information is obviously being sent from the Linux machine so that the Windows installation can make use of it.  And, when I copy files between the two Linux machines, the copying speed is abysmal.  I'm currently copying a file, and getting 161 kB/s.

First, I found posts of users claiming it was the fact that /proc/sys/net/ipv4/tcp_window_scaling was turned on, and after I switched it off, my network speed shot back up to the roughly 12.5 MB/s that it was supposed to be, but after a few days, it's back to it's previous copying speed.

I know my thread heading was a little baiting, it's just that I've been battling this problem on and off for a very long time now, so I was hoping to draw more eyes to the post.  Sorry for that.

---

