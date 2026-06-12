---
title: "media server file system"
date: 2008-09-19
forum: Multimedia Software
---

### Post by tone33 on 2008-09-19
I'm setting up a linux media server (quite possibly an ubuntu flavor) and am trying to decide on a file system.  I like XFS, but would also like to be able to access it from a windows pc.  In order to meet the windows requirement am I required to use NTFS??  And what are the real drawbacks with using NTFS over XFS?  or some other linux file system.

---

### Post by Martje_001 on 2008-09-19
It doesn't matter what filesystem you choose. You problably are going to share with SAMBA, which has nothing to do with it.

---

### Post by tone33 on 2008-09-20
so samba will allow windows to see XFS?

---

### Post by Martje_001 on 2008-09-21
It will see it, but not as XFS. It sees it as a SAMBA share.

(so yes, it will see your files & folders)

---

### Post by tone33 on 2008-09-21
can it read and write to it?  It'd be ok if i can't write, but I would like to be able to read.   so I'll have a windows machine with Media Player and would like to play mp3's from the XFS (samba) share.

---

### Post by Martje_001 on 2008-09-22
If you give permission to write and read, it will. 

Read this: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by aeiah on 2008-09-22
basically it looks like this if it makes it clearer:

```


 [------samba-------]
 [-linux filesystem-]
 [----hard drive----]
###### computer ######


```

windows clients communicate with samba, not the actual file system. samba knows how to write to anything that linux knows how to write to, so you can choose which one is best for you in terms of speed, reliability etc. in truth it isnt that important because it isnt gonna be under much stress.

---

### Post by tone33 on 2008-09-22
ah ok i see now.  So it's just an interface to the linux FS.  Thanks for the explanations and links.

---

