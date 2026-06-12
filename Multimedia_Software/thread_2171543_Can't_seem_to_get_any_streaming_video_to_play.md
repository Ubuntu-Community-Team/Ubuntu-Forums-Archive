---
title: "Can't seem to get any streaming video to play"
date: 2013-08-31
forum: Multimedia Software
---

### Post by Peter_Bard on 2013-08-31
I wanted to set up a computer to my television to watch all of my television content (long story, don't worry about it). I bought and Asus Eeebox, EB1033 with Ubuntu 12.04. My plan was to use all of my streaming video options to watch my television content through the computer. Most notable, I needed xfinity.com's video to load. I went into their site to try to get it to work, and I get "Obtaining authorization," and then "Starting playback," and then it just continues to not load indefinitely.

Weirdly, I went to turn the computer off while this was happening once, and as soon as I confirmed that I wanted all programs to close, the video started working, as though another program that was running was preventing the video from loading. I'm thinking I'm going to try to load Windows if I can't get this to work soon.

---

### Post by SeijiSensei on 2013-08-31
Some commercial services like Amazon Instant require the now-deprecated **hal** and **libhal1** packages be installed to handle digital rights management.  That doesn't seem like your problem, though.  Maybe you just didn't have enough free memory?  How big a swap file are you using?  It should be at least as large as physical memory.

---

### Post by Peter_Bard on 2013-08-31
I don't know what you mean by swap file. How can I check that? Can I change it?

---

### Post by SeijiSensei on 2013-08-31
Sure.  Run top and see what it reports.  Here's mine:

```

$ top
top - 22:42:35 up 1 day, 12:03,  4 users,  load average: 1.82, 1.84, 1.74
Tasks: 223 total,   3 running, 220 sleeping,   0 stopped,   0 zombie
%Cpu(s): 34.0 us,  8.3 sy,  0.0 ni, 57.6 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem:   8123988 total,  5412320 used,  2711668 free,   326060 buffers
KiB Swap:  3998716 total,        0 used,  3998716 free,  3499032 cached

```

I have about 4 GB allocated to swap.  With 8GB of physical memory, none of the swap on this machine is in use.  The "cached" entry is deceivingly located.  It is actually reporting the amount of physical memory devoted to caching disk transactions.  Linux is quite aggressive about caching for performance reasons.

The norm is to create a separate partition for swap at installation, but you can also [create a regular file]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/") for swap if you didn't allocate it before.

---

