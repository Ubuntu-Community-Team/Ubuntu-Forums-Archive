---
title: "Symbolic Link Paths Don't Work Over Network"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by tracyandskye on 2010-09-17
I'd like to create symbolic links on our server which will work from any work station.  I guess the problem is that they use absolute paths.  Since the absolute path is different from each workstation, they don't work except for the computer on which they were created.  Is there a way to make them use relative paths instead?

---

### Post by crokett on 2010-09-17
Why can't you mount the remote share on the server in the same place on each workstation?  I mean, if I mount the samba share on my desktop in, say /media/samba on one machine, then create a link and move that link to another machine as long as the same share is mounted in /media/samba on the 2nd machine I expect it would work.

---

### Post by tracyandskye on 2010-09-19
Ah!  Of course!  That gets me out of the home folder which is the problem.  That will work with our 'buntu machines, but I assume the links still won't work from our one XP workstation.

---

