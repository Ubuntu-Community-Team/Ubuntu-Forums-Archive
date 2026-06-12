---
title: "Lenovo 3000 N100 sound problem after &quot;fuse&quot;"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by imagine.animesh on 2007-07-24
I don't know if these two events are related, but I somehow have lost sound on my kubuntu after a useless installation of fuse. (came along with sshfs).
The reason why I suspect of their connection, is because "fuse" forced me out of the sudoers file as well, which I fixed separately.

Now, I have followed the instructions in these posts and the comprehensive guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[http://ubuntuforums.org/showthread.php?t=352614](http://ubuntuforums.org/showthread.php?t=352614)

Nothing came to rescue.

kmix gives a weird error when you go to  change volume or mute the speakers:
"It seems that kmix is not running"

Any thoughts?

---

### Post by imagine.animesh on 2007-07-24
Hello Friends!!!
Just got out of the hot water.
It seems notorious fuse had removed me from the audio group and no sound cards were available for my use!!

added my user name to the audio group in /etc/group and rebooted.

Amarok rocking again!!
Cheers!

---

