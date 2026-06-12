---
title: "multiple directories and ushare"
date: 2010-11-20
forum: Multimedia Software
---

### Post by Gh3ttoman on 2010-11-20
Ushare has been working great, but i have one problem. Only the first directory gets shared with my xbox 360.  is there a way to fix this? or is there something better to use than ushare?


edit: more details: i have my fstab working with uuid's instead of directories. and ushare does pick up all the files, its just that they all don't show up on the xbox, just the stuff from the first hard drive. i have four different hard drives im trying to share in total, and they all automount at boot.

---

### Post by Gh3ttoman on 2010-11-22
No one else has encountered this problem?

---

### Post by Chris Riley on 2011-01-03
Yeah, I got the same problem; all my directories are on one drive though.

the line in ushare.conf:

[COLOR="Red"]USHARE_DIR=/home/chris/media/Videos/,/home/chris/media/Music/,/home/chris/media/Photos/,/home/chris/media/Pictures/
[/COLOR]
ushare recognises all of them, and reports that thousands of files have been found, but xbox only sees the files in the first directory.

I would apreciate it if someone could give me a hint.

:confused:

---

### Post by NerdWermz on 2011-02-20
I am having the same issue, all my folder are on different drives though, but xbox only sees the videos in the first folder.

---

### Post by nubias on 2011-02-21
I had a problem similar to this.

It seemed to be a problem with sharing multiple dirs in the ushare.conf file.

What I ended up doing is making a folder with virtual links to all my shares and just putting a link to that one entry in my ushare.conf file.

---

