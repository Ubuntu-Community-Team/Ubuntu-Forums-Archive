---
title: "gnump3d problem"
date: 2008-08-14
forum: Multimedia Software
---

### Post by arluijen on 2008-08-14
Newby here. Installed gnump3d out of the box to share mp3's over my lan. Starts up just fine but it doesn't play any file, it stops after a second or so trying. Either on the ubuntu (hardy) machine or any other on the LAN.

The error log shows:

Cant open '/var/music/<name of file here>.mp3' : Permission denied at /usr/bin/gnump3d line 2006.
binmode() on closed filehandle FILE at /usr/bin/gnump3d line 2007.
read() on closed filehandle FILE at /usr/bin/gnump3d line 2024.
Header: ICY 200 OK

I haven't changed any of the default settings and just copied a bunch of mp3's to the /var/music, of which gnump3d is owner. 

Ideas ?

---

