---
title: "Workaround - Random missing files on samba shares"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by callan79 on 2009-11-03
In a previous thread - [here](http://ubuntuforums.org/showthread.php?t=1281411) - I posted about a problem in karmic where network cifs shares mount, but random files are missing in random directories. The shares are mounted with cifs, using the nounix mount option.

For example a directory may show 100 files, when it really has 500 files. If you look at that same network share using a jaunty system, all 500 files show up.

Even stranger is that although the files don't show up in a directory listing, it's actually possible to access them manually if you know the filename.

Anyway, I really just wanted to post a workaround that I found after many hours of searching!

The workaround is to add noserverino to your mount options - fixed it for me!

More info here - [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/406466](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/406466)


Hopefully this info makes life easier for at least one more person out there ...

Cheers
Callan

---

### Post by MelIrizarry on 2009-12-01
This workaround solved my problem with CIFS mounted shares.  

Thanks for the link to the solution.

I could create a directory name D111 and I would see it fine.  But if I changed it to D1111 it would disappear from file browser and ls.  I could still cd into it by it would not show up in listings.  Changing it back to D111 would allow it to show up again.

Had a crazy time trying to figure this out, glad it was a simple parameter to the mount.

Mel

---

