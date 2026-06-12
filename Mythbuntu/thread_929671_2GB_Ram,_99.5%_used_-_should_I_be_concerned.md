---
title: "2GB Ram, 99.5% used - should I be concerned?"
date: 2008-09-25
forum: Mythbuntu
---

### Post by SiHa on 2008-09-25
Not sure if I should be worried.

By BE/FE hs 2GB ram. After rebooot, system stats show ~20% usage. I've noticed that some time (1 day+?) later the memory usage shows 99+% used, about 15MB free.

Should I be concerned? I'm used to Windows that seems to use 1GB of swapfile even when there's over 1GB free RAM - perhaps Linux is just a bit more intelligent than that? The BE does hang from time to time, after 5+ days up-time. I'm not too bothered about this, and it doesn't seem to be related to the memory usage.

So - should I worry, or is this normal, that Myth will use all the RAM available?

Thanks,

Simon

---

### Post by onero on 2008-09-25
Have you checked which programs are using all the RAM? Maybe one of them is leaking memory. In general though, you probably shouldn't be worried; usually the memory used is actually just disk cache. This page has a pretty good explanation: [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by superm1 on 2008-09-25
> **SiHa said:**
> Not sure if I should be worried.

By BE/FE hs 2GB ram. After rebooot, system stats show ~20% usage. I've noticed that some time (1 day+?) later the memory usage shows 99+% used, about 15MB free.

Should I be concerned? I'm used to Windows that seems to use 1GB of swapfile even when there's over 1GB free RAM - perhaps Linux is just a bit more intelligent than that? The BE does hang from time to time, after 5+ days up-time. I'm not too bothered about this, and it doesn't seem to be related to the memory usage.

So - should I worry, or is this normal, that Myth will use all the RAM available?

Thanks,

Simon
Yeah Linux will use all your available RAM for caching.  Might as well, it's just going to waste otherwise.

---

### Post by SiHa on 2008-09-25
Yeah, what I reckoned. As I said, I was just concerned as I'm used to windows that just lets most of the RAM go to waste. F'rinstance - I'm typing this from an XP box. There's 1.4GB Free, but it's still using 416MB swapfile!

Panic over...

Onero - thanks, the only things running are the various Myth processes.

---

### Post by Alejandro Nova on 2008-12-30
Sure. In my Ubuntu laptop I've got 2.5 GB, and the real memory usage (used-cached) is around 380 MB. So, I know Linux is going to use my available memory for cache. The question: How can I speed up my programs with the additional RAM? Is there something I can do about it? I already tried swappiness=0. shmfs /tmp? How about that?

Thanks in advance ;)

---

