---
title: "Why is ESounD not mixing OSS output?"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by Fibonacci on 2006-11-04
Hello,

I've noticed that whenever any application outputs sound through OSS, all possibility of sound output by any other application is instantly killed. Even if ESD is running.

So what, you might ask, isn't that how it's supposed to work? Well, it certainly isn't how it has worked for me on other distros. On Fedora Core, for example, ESD (activated through System -> Preferences -> Sound) makes Adobe Flash, MPlayer, Xine, and even [Second Life]("http://www.secondlife.com") work in harmony, even generate simultaneous sound output; none of them directly opens /dev/dsp. This, unfortunately, is not the case on Ubuntu - Flash player directly opens /dev/dsp, even with ESD running, and no other application can generate sound output from them on.

Before anyone mentions it, I do know about aoss. I know it generates far more problems than it solves - namely, making Firefox hang if it has been opened for a long time. So I don't want that, I just want ESounD (or any other thing that can make Flash work together with MPlayer - I'm open to suggestions) to work properly. What can I do?

Thanks in advance,

-Fibo

---

