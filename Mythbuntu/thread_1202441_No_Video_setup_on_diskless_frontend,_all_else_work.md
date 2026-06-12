---
title: "No Video setup on diskless frontend, all else works"
date: 2009-07-02
forum: Mythbuntu
---

### Post by hsnape on 2009-07-02
After spending quite  bit of time getting a diskless frontend "working" I finally have a system that boots off the net, and connects to a backend. However it only seems to work for watching live TV and recordings, there doesn't seem to be a way of using the backend's videos. In fact Setup/Utilities just has a setup menu, no video setup. Normally I have been nfs mounting the server's /var/lib/mythtv/videos directory on the client and everything works. But in this incarnation, the frontend seems to be configured in such a way that it doesn't do videos at all??

Any help appreciated.

---

### Post by Verzweifler on 2009-07-02
Have you enabled/installed mythvideo on the mythbuntu-control-centre GUI?
I had a similar issue with mythmusic, which was not there by default, but after setting it on the GUI, it got installed and worked as expected...

---

### Post by hsnape on 2009-07-02
Yup, had to install mythvideo, who would have guessed that installing the frontend gave you a frontend to just tv and recordings...

Now all I have to do is figure out why fstab gets rewritten, even though the lts.conf sets this to false and the diskless /var/lib/mythtv/videos gets an empty directory instead of the symlink I created prior to creating a new squashed image. I like undocumented magic. It's like an adventure game.

---

### Post by Verzweifler on 2009-07-03
That fstab-issue also drove me nuts...

I solved it by manually mounting the nfs-shares in /etc/rc.local 
Watch out! You need to have installed nfs-support to be able to mount them (*sudo apt-get nfs-common nfs-kernel-server* should do the trick!) and I have to use *mount **-n** -t nfs ...* because my diskless complained about write-protected mtab...

---

