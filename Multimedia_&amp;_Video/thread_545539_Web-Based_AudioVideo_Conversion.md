---
title: "Web-Based Audio/Video Conversion?"
date: 2007-09-07
forum: Multimedia &amp; Video
---

### Post by Megatog615 on 2007-09-07
Is there some way I can set up a web-based audio/video conversion site on my Apache HTTP server, that interfaces with mencoder, or ffmpeg, or something? I want to be able to connect to it from any computer in the house and convert videos and music files, from any operating system.

Has anyone made something like this?

---

### Post by kidders on 2007-09-08
Hi there,

I'm not so sure a web-based application would be the right approach. I can't help wondering how well web browsers & servers would handle HTTP POST requests with hundreds of megabytes (or perhaps several gigabytes) of data in them. Additionally, since any media conversion would surely have to be performed asynchronously anyway, I can't quite see how involving HTTP would serve much of a purpose.

If you wanted to, you could certainly give it a try, but I would probably opt for something more conventional, personally. Perhaps a standard network share (ie a dropbox of sorts), and a conversion process handled by cron?

---

### Post by Megatog615 on 2007-09-09
Well it was only going to be for my home network, and not for millions of users to play with ;).

---

