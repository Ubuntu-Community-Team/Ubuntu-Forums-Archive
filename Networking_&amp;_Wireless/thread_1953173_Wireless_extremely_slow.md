---
title: "Wireless extremely slow"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by iniquiTrance on 2012-04-05
I just installed ubuntu 11.10 on a dell XPS laptop, and the wireless is extremely slow. 

I'm talking sub 1 kb/s slow. 

I was previously running 11.10 through Wubi, where it was working fine, but had to reformat, and am now running it on its own partition. 

The wireless card is an Intel Centrino Advanced-N 6200. wlan0 seems to be using iwlagn as the driver.

The wifi works fine from windows 7. 

Any ideas what could be causing this?

---

### Post by iniquiTrance on 2012-04-05
Ok, this seemed to have worked as a workaround.

I followed the instructions in this post here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836250/comments/23](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836250/comments/23)

Seems it's a common bug.

---

