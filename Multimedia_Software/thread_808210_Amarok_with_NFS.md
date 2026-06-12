---
title: "Amarok with NFS"
date: 2008-05-26
forum: Multimedia Software
---

### Post by otwr on 2008-05-26
I have a basement machine that stores all the media files, which are shared via NFS to the various machines upstairs. The Amarok database is also hosted with MySQL on the downstairs machine. The issue goes like this:

- Amarok autostarts before wireless is ready
- Therefore the NFS mounts are not active, and Amarok concludes there is no collection
- Amarok doesn't seem to be aware of when the NFS mount becomes active
- You can either do a "Rescan collection" which is time-consuming, or (I found this out recently) you can shut down and restart Amarok and the collection will reappear.

It's a little annoying to shut down and restart Amarok in order to see the collection; so I was wondering what sort of other solutions people have come up with for centralizing their music collections... or is there a way to prevent Amarok from autostarting before there's a network connection available?

---

### Post by otwr on 2008-05-26
New title bump

---

### Post by xc3RnbFO8P on 2008-05-26
Some thing like this?
[http://ubuntuforums.org/showthread.php?t=339732]("http://ubuntuforums.org/showthread.php?t=339732")

---

