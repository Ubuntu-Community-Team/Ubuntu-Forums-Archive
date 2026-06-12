---
title: "How do I get the 'Motion' daemon to stop?  And take up space on the hard drive."
date: 2013-05-16
forum: Multimedia Software
---

### Post by psyllex on 2013-05-16
Hello fine people.  I'm using motion to run a webcam off my Ubuntu 12.04 LTS server.  It works good (not great) but it'll serve my purposes.  The question is how to get the daemon to stop.  I don't want to have it running all night.  And I'm not sure if the snapshots are going to use up all my harddrive space or not.  I attempted ```
sudo service motion stop
``` ; s```
udo /etc/init.d/motion stop
``` ; then i used ```
ps aux | grep motion
``` and killed all the processes associated and I still couldn't get it to shut down.  Anyone able to help out?

---

### Post by Pinoy Tux on 2013-05-17
Looks like all you need to do is do the reverse [here]("http://www.youtube.com/watch?v=ZAoA_J5HD0M") (timestamp 4:07).

---

