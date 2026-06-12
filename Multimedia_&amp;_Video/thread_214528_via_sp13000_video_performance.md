---
title: "via sp13000 video performance"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by ajlapp on 2006-07-12
I'm building a linux box for the first time.  This will eventually be a MythBox for my tv room....in the meantime it is running Ubuntu.

via sp13000
1GB super talent RAM
direct ethernet connection

glxgears is showing a peak of 60 frames per second.

is this normal?  the system struggles to play any video files.  the performance is dismal.

how do i guarantee that the via drivers are detected correctly and that they are working?  if they are not there how do i put them there and get this machine performing like it did with XP?  Thanks.

---

### Post by rvfh on 2006-08-20
Make sure your video player uses the XvMC video driver to play MPEG streams.

I use Kubuntu and only xine (apt-get install xine-ui) seems to use it (Kaffeine complains, as usual). You can use xine in [G]Ubuntu too.

Good luck,
Hervé.

---

