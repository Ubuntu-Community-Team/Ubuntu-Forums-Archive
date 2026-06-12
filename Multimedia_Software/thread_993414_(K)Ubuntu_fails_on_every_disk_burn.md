---
title: "(K)Ubuntu fails on every disk burn"
date: 2008-11-25
forum: Multimedia Software
---

### Post by slimjim8094 on 2008-11-25
I've made twenty coasters so far trying to burn Ubuntu 8.10 for a friend.

I've tried K3B, Brasero, Nero Linux (trial), and cdrecord from the command line. I've tried replacing wodim (fake cdrecord) with real cdrecord. I've tried two different types of CD-Rs

All the burns go the same way - they all burn fine, but all fail on verify. Some get further than others.

This is Kubuntu 8.10, with today's kernel update and with the previous kernel. My CD-drive is /dev/scd0 or I guess alternately /dev/sr0. I've never manually set it.

This is a laptop with a slimline-style CD/DVD burner. I've never had problems under windows burning exactly the same ISOs.

It seems like this may be a known problem, but all the workarounds I've seen don't work. Any guesses?

Thanks!

EDIT: Just to be clear, the md5sums on the ISOs work out alright. I also downloaded them through bittorrent, so it's not the ISO's problem but strictly a burning issue.

EDIT2: May be unrelated, but K3B is using a lot of the CPU. I'm burning a disk right now, and the interface is very sluggish/catch-up. It's also having trouble keeping both (device and software) buffers full. never had that problem on windows. DMA perhaps?

---

### Post by Zaraphrax on 2008-11-25
Have you tried burning the discs at a slower speed?

---

### Post by slimjim8094 on 2008-11-25
Yes; the minimum allowed by k3b is 10x for my drive. I'll try nero at a slower speed, with the new disks.

---

### Post by SuperSonic4 on 2008-11-25
k3b is doing a heavy task - it will use a lot of CPU

Have you tried the discs you've burnt anyway, ones that have failed to verify on mine have worked as normal

---

### Post by slimjim8094 on 2008-11-25
I just tired nero as root, and verifyy failed at the same spot as last time (33%)

The MD5sum went mostly ok, but failed on "Input/Output error" for a number of files. (ironically, the nautalis-cd-burner deb was one of them)

I'm going to see if it installs. Even if it does, this issue is not fixed... I literally haven't had a single sucessful burn.

---

### Post by slimjim8094 on 2008-11-25
OK. I had a single sucessful burn; a 10M netboot ISO image for Ubuntu. That's enough to bootstrap it as my friends card is supported. The disk verified and md5sum'ed.

But Ubuntu not being able to burn its own disk is embarassing. I'm thinking it may be a kernel issue as most people with application/subsystem (wodim vs cdrecord) report Nero as working, since it directly interfaces with the hardware.

Are there any fancy kernel boot parameters? I'm on SATA natively, as far as I can tell... if that matters. Or have I found a bug?

---

