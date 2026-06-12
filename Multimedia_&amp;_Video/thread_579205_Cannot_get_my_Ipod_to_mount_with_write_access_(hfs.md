---
title: "Cannot get my Ipod to mount with write access (hfs+)"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by pormogo on 2007-10-18
Some months ago I went through the trouble of reformatting my ipod info hfs+ (without journaling disabled). Now I could use it with my laptop and my desktop machine. Since I did the update I have been using amarok to exclusively manage the ipod. Sometime last week while I was connected to the ipod amarok crashed and the lockfile remained on the ipod (nano G2). Next time I plugged it in I noticed it mounted as readonly. I thought that was odd but the automounter did it so I figured it could just be a mistake. I unmounted it and remounted it using

*mount -w -t 'hfsplus' /dev/sde3 /media/Ipod*

and it looks like it mounts correctly
[I]
 /dev/sde3 on /media/Ipod type hfsplus (rw)
[/I]
however I still can't delete that stupid lockfile or create new files in the ipod itself

[I]rm -f iTunesLock 
rm: cannot remove `iTunesLock': Read-only file system
[/I]
huh??? It looks to be mount (rw) to me... I'm logged in as root..... Has anyone else seen anything like this. I haven't plugged my ipod into my laptop since I reformatted it. It has only been plugged into 2 computers. My Ubuntu 7.04 Box and a Windows XP box I use to charge it at work (which can't even read it). Suggestions?

---

### Post by F-3582 on 2007-12-09
Did you try mounting it on a Mac? At least to remove the lockfile...

---

