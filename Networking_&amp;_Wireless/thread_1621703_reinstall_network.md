---
title: "reinstall network"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by toolmania1 on 2010-11-14
How can I reinstall network.  I remove dhclient3 because chkrootkit identified it as a possible issue.  Well, now I have no internet.  I am running from the live cd for ubuntu right now.  

I also posted in another part on this forum earlier.  I was told to copy files.  I tried to copy files but was unsuccessful.  I did not see 'dhclient3'.

Is there a way I can reinstall the all of the network part for ubuntu?

I can just reinstall all of ubuntu, but I have some pictures on the drive now that I do not want to lose.  Also, unfortunately, I do not have enough storage as I am out of dvds and the usb drive I have is too small to hold all the movies that we recorded with the digitial camera.  

I am new to Ubuntu within the last 2 weeks.  I have learned a lot.  I installed SELinux, Chkrootkit, ClamAV, AIDE, and set up UFW firewall.  I wrote it all down, so I can do all of that again if needed.  I just don't want to lost my videos / pics.

---

### Post by NIN101 on 2010-11-14
Hello,

when booted from the LiveCD, try to mount the root directory of the installed ubuntu, if it wasn't already done by ubuntu automatically. 

Then, as a root in the LiveCD, run
```
chroot /media/[mountpointofubuntupartition]
```

after that,

run:
```

apt-get update
apt-get install dhcp3-client.
```

Not tested, but should work.

---

### Post by toolmania1 on 2010-11-14
I had tried something else, but it did not work.  I got the data off the pc, then just reinstalled ubuntu from scratch.

---

