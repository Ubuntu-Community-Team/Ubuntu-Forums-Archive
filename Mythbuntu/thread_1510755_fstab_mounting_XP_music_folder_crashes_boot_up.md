---
title: "fstab mounting XP music folder crashes boot up"
date: 2010-06-15
forum: Mythbuntu
---

### Post by larsolav on 2010-06-15
Hi all.
I have all my music on an XP machine.
When I add this line to /etc/fstab:
> //192.168.1.66/My\040Music /var/lib/mythtv/music cifs   Lars,_netdev   0 0
and do "sudo mount -a" I then have access to my music in Mythmusic.
However, when I then reboot, boot up completely freezes up like in my earlier post: [http://ubuntuforums.org/showthread.php?t=1472280](http://ubuntuforums.org/showthread.php?t=1472280). Luckily I installed 10.04 to a compact flash drive and could pull it out and edit fstab via a compact flash reader on an other machine...
Now I just manually mount the folder using this command after each potential reboot:
```
sudo mount -t cifs "//192.168.1.66/My Music" /var/lib/mythtv/music -o Lars,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

Now, is there a way I can run this mount command automatically after everything else has loaded up?

Thanks!

---

### Post by ian dobson on 2010-06-16
Hi,

I've got a feeling that the \040 (space in My Music) is causing fstab/mountall to blow a fuse. The best thing to do is place the mount command (exactly as you've shown it) in your /etc/rc.local file. This file is called after most other things have been run so you should be safe.

I've been running my MythTV frontend with a mount command in rc.local for almost 2years now without any major problems.

Regards
Ian Dobson

---

### Post by larsolav on 2010-06-16
Thanks Ian!
I'll give that a try tonight. Sounds like a simple and elegant solution!

Sincerely,
Lars

---

