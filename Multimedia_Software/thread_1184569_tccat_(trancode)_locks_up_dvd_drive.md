---
title: "tccat (trancode) locks up dvd drive"
date: 2009-06-11
forum: Multimedia Software
---

### Post by Seth Kriticos on 2009-06-11
Hello there,

I'm just backing up some of my DVD's and the dvd:rip program in combination with transcode locks up the drive once in a while. The origin of the problem is, that tccat (transcode) keeps a file descriptor to /dev/dvd and this effectively lock up hardware and software eject.

'lsof /dev/dvd' shows the open file descriptor.
Killing tccat with 'kill -9 <pid>' (pid optained from lsof) solves the problem until the next lockup.

Did not found a current bug report for it, so I just post it here.

System: Ubuntu Jaunty (9.04), x64

---

