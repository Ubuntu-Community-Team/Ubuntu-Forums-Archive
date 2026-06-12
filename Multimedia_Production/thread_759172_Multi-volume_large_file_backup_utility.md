---
title: "Multi-volume large file backup utility"
date: 2008-04-18
forum: Multimedia Production
---

### Post by jharr on 2008-04-18
I have a fairly large file server (2.1TB) containing mostly media files. I've been using rsync to backup to a 1TB external drive. It has worked for me since I've been backing up a small amount of data (<1TB), but now I've pushed past that. So I was looking at doing multi-volume backups now and I wanted to see what everyone else uses.

Here's some stuff that I want/have run into:
- I have tried using unionfs to merge two 1TB drives for backup, but unionfs has some strange delete semantics (delete=all option doesn't work with mount) that makes the volumes balloon up when I use it. On top of that, when the top filesystem fills up, it doesn't move onto the next one, it just stops.
- I would like the backups to be easily readable (IE - regular filesystem). 
- LVM/raid0/extended disks is not an option.
- I would like it so that not all of the volumes have to be plugged in to do a backup or view of files.

Ultimately, this would be the coolest backup utility for me:
- For the most part, it is just rsync. But it will operate on multiple volumes, only one of which is mounted at a time.
- When one backup volume is filled, it will move on to the next.
- If a file is deleted from the regular filesystem, then it should be deleted from one of the backup volumes as well. Then that freed space should be reused.

Anyone have ideas? Anything close? If not, I'm might start writing my own...

Thanks!

---

