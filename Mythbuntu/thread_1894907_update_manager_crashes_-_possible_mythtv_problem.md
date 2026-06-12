---
title: "update manager crashes - possible mythtv problem"
date: 2011-12-13
forum: Mythbuntu
---

### Post by Ubu_Fester on 2011-12-13
For the last few months, every time update manager runs (either script or through the UI), it ends with an error pointing to a mythtv problem and that the package update did not complete.

Error says:
[PHP]mythtv-common script returned error exit status 128[/PHP]

I originally suspected a permissions issue, since I was setting samba up to read a mythtv directory.  I have tried to check permissions with the mythtv group user, but don't see any problems.

I have spent hours looking for old posts and solutions.  What types of checks can I make to diagnose?  

Running ubuntu 10.10 and mythtv 23.1

---

### Post by nickrout on 2011-12-13
```
sudo apt-get install mythtv-common
``` ?

---

### Post by Ubu_Fester on 2011-12-13
Thanks for your assistance.  Here's the first few lines of messages after "sudo apt-get install mythtv-common"

[PHP]Setting up mythtv-common (0.23.1+fixes26437-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess installed post-installation script returned error exit status 128
dpkg: dependency problems prevent configuration of mythtv-transcode-utils:
 mythtv-transcode-utils depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-transcode-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
[/PHP]

---

### Post by nickrout on 2011-12-13
> **Ubu_Fester said:**
> Thanks for your assistance.  Here's the first few lines of messages after "sudo apt-get install mythtv-common"

[PHP]Setting up mythtv-common (0.23.1+fixes26437-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess installed post-installation script returned error exit status 128
dpkg: dependency problems prevent configuration of mythtv-transcode-utils:
 mythtv-transcode-utils depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
dpkg: error processing mythtv-transcode-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
[/PHP]

ummmm try

```
sudo dpkg-reconfigure mythtv-common
```

---

### Post by Ubu_Fester on 2011-12-13
Results are:  

[PHP]/usr/sbin/dpkg-reconfigure: mythtv-common is broken or not fully installed
[/PHP]

BTW, this has been like this for awhile.  Mythtv works fine, I'm just not getting ANY updates installed -- which is now affecting other Ubuntu updates....

---

### Post by nickrout on 2011-12-14
you are beyond my apt-fu. You could try ```
dpkg --configure mythtv-common
```

---

### Post by Ubu_Fester on 2011-12-14
Results:

[PHP]Setting up mythtv-common (0.23.1+fixes26437-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess installed post-installation script returned error exit status 128
Errors were encountered while processing:
 mythtv-common
[/PHP]My thoughts now are:
 - backup mythtv database
 - wipe mythtv
 - clean reinstall of mythtv
 - restore database

But if there are some simpler diagnostic tests or other ways to reinstall, I'll try those first.:confused:

---

### Post by nickrout on 2011-12-14
> **Ubu_Fester said:**
> Results:

[PHP]Setting up mythtv-common (0.23.1+fixes26437-0ubuntu1) ...
dpkg: error processing mythtv-common (--configure):
 subprocess installed post-installation script returned error exit status 128
Errors were encountered while processing:
 mythtv-common
[/PHP]My thoughts now are:
 - backup mythtv database
 - wipe mythtv
 - clean reinstall of mythtv
 - restore database

But if there are some simpler diagnostic tests or other ways to reinstall, I'll try those first.:confused:

probably no need to backup the database, but no harm either.

---

### Post by andree_b on 2011-12-15
> **Ubu_Fester said:**
> 
My thoughts now are:
 - backup mythtv database
 - wipe mythtv
 - clean reinstall of mythtv
 - restore database

But if there are some simpler diagnostic tests or other ways to reinstall, I'll try those first.:confused:

May be try upgrading to 0.24 instead of wipe+reinstall?

---

