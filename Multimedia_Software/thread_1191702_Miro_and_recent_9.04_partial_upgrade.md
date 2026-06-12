---
title: "Miro and recent 9.04 partial upgrade"
date: 2009-06-19
forum: Multimedia Software
---

### Post by sefs on 2009-06-19
Hi all,

I woke up this morning june 19th 2009 to a partial upgrade of 9.04 which removed libtorrent-raster2 and miro and left miro broken and un-installable.  

Has anyone experienced this?  And what is the fix.

Thanks.

---

### Post by dalesd on 2009-06-25
I have the same issue, though I haven't gone ahead with the partial upgrade yet.  Update manager wants to remove Miro and libtorrent-rasterbar2 before it can install 2.6.28-13

Have you learned any more about the issue?

---

### Post by Arup on 2009-06-25
I install Miro from their repos rather than Ubuntu repos and so far no such issues like the one mentioned above. Miro repo can be found at this page [http://www.getmiro.com/download/for-ubuntu/](http://www.getmiro.com/download/for-ubuntu/)

---

### Post by dalesd on 2009-06-25
I double-checked my sources.list, and the Miro repo was already there.

---

### Post by dalesd on 2009-06-26
I went ahead with the partial upgrade, which removed Miro and libtorrent-rasterbar2.  Then I tried to reinstall Miro (from the Miro repository) and it won't install.  
```
$ sudo apt-get install miro
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
miro: Depends: libtorrent-rasterbar2 but it is not going to be installed
E: Broken packages 
```

---

### Post by dalesd on 2009-06-27
I solved my issue.  It was a conflict with Deluge, installed from the (unofficial) Deluge repository.  Once I removed that I was able to reinstall Miro.  Then I removed the Deluge repo and installed Deluge from the Ubuntu repo.

---

