---
title: "[SOLVED] video colours messed up"
date: 2008-07-27
forum: Multimedia Software
---

### Post by clarknova on 2008-07-27
Recently my colours are messed up when playing videos. This appears to be application-independent, it happens in totem, vlc and xine on many filetypes. It is also affecting both users on this machine.

It appears as though red and green are reversed. See the screenshot of the free movie "Big Buck Bunny".

I'm using Ubuntu 8.04.1 x86_64 up to date with the latest binary driver from nvidia.com (173.14.09). This problem began about a week ago, but I don't think I've seen a kernel update in 3 weeks or so, and the nvidia driver was installed at least a month back.

Any ideas?

db

---

### Post by mc4man on 2008-07-27
Try links from here
[http://ubuntuforums.org/showthread.php?t=869210&highlight=wrong+colors](http://ubuntuforums.org/showthread.php?t=869210&highlight=wrong+colors)

---

### Post by clarknova on 2008-07-27
sudo apt-get purge gxine did it for me.

db

---

