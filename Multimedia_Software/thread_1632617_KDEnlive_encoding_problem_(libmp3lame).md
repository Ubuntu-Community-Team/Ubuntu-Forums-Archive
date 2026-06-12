---
title: "KDEnlive encoding problem (libmp3lame)"
date: 2010-11-28
forum: Multimedia Software
---

### Post by Benjamin Hawk on 2010-11-28
Hello folks.

This is my first post in this forum.

After trying out every video compositing program I found for Linux, I am about to settle with KDEnlive. It looks like the best allrounder professional program in this section to me.

I only got one problem. I cant encode files with mpeg-4. All options here are grayed out and if I hover over one of the options for a moment it's going to tell me:

"Unsupported audio codec: libmp3lame"

Whats funny is that it worked a time before i reinstalled my system.
I also checked and I got libmp3lame installed. So why has KDEnlive problems to access this library?

Anyone got an idea?

---

### Post by Yellow Pasque on 2010-11-28
If you're trying to encode, you need lame package.

---

### Post by Benjamin Hawk on 2010-12-30
stumpled over this old post of mine.

I just didn't realize these days that I had to run the configuration wizard of kdenlive one more time after getting all the needed librarys.

Thanks though Temüjin. Not having installed the lame package also was a fault I made.

---

### Post by cips42 on 2011-11-09
Thanks for this hint, after rerunning the configuration wizard, I finally managed to encode videos with an mp3 audio track.

Ubuntu 11.10 / Kdenlive 0.8.2-0ubuntu0~sunab~oneiric2 / libmp3lame0 3.98.4-0ubuntu1

---

