---
title: "How I Solved My Nvidia woes"
date: 2008-05-15
forum: Multimedia Software
---

### Post by eosha on 2008-05-15
I've been beating my head against this for a month, and I finally got it!

I tried every method of installing the nvidia drivers I could find: scripts, synaptic, download from nvidia, everything. I tweaked and tweaked and tweaked, and they still didn't work.

Tonight, I found the solution [here]("https://answers.launchpad.net/ubuntu/+question/30999").

When I had upgraded from 7.10 to 8.04, somehow my grub menu.lst hadn't been updated. So I had unknowingly been running the old 2.6.22-14 kernel instead of 2.6.24-16. 

I edited /boot/grub/menu.lst and changed all the references from 2.6.22-14 to 2.6.24-16, rebooted, and installed the drivers through the "restricted hardware drivers" menu. And it worked!

---

