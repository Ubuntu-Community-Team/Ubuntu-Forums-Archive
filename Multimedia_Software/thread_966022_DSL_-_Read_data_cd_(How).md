---
title: "DSL - Read data cd (How?)"
date: 2008-11-01
forum: Multimedia Software
---

### Post by Jynxxander on 2008-11-01
Help me please. How can I get DSL to read a data cd?
Like, with wallpapers on it. (Cause the computer that DSL is on is not connected to the internet)

---

### Post by cariboo on 2008-11-01
To read a data CD it works the same as any other Linux distribution. If you are running DSL off of the CD I not sure if it is going to work if you remove the CD, I installed DSL to my hard drive.

to mount a CD in a terminal type:

```
mount /dev/cdrom /mnt

```
This assumes you are running as root.

Jim

---

