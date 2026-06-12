---
title: "sshfs:  &quot;df -h&quot; reports incorrect sizes, so I can't copy files using nautilus"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by scurry7 on 2009-02-04
hello all,
so I mount to a remote server using sshfs, I love it, but when I try to copy files over to it it will not let me.  I try to copy files to it using nautilus and I get this error:
```
There is not enough space on the destination. Try to remove files to make space.
```
But there is plenty of space (a few TBs)

how can i fix this so I can copy things to the mounted sshfs?

---

### Post by albinootje on 2009-02-04
> **scurry7 said:**
> when I try to copy files over to it it will not let me.  I try to copy files to it using nautilus and I get this error:
```
There is not enough space on the destination. Try to remove files to make space.
```
But there is plenty of space (a few TBs)


Can you try another file manager like thunar, pcmanfm, konqueror to see whether this is a Nautilus bug ?

Meanwhile check the sshfs faq :
[http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq)

And check whether a bug has been reported already :
[https://bugs.launchpad.net/bugs/+bugs?field.searchtext=nautilus+sshfs&search=Search+Bug+Reports&field.scope=all&field.scope.target=](https://bugs.launchpad.net/bugs/+bugs?field.searchtext=nautilus+sshfs&search=Search+Bug+Reports&field.scope=all&field.scope.target=)

---

### Post by Dougie187 on 2009-02-04
Couldn't you try just doing cp from a commandline?

---

### Post by thegner on 2009-02-04
I am experiencing the exact same issue.

cp from command line works, nautilus does not.

I can open files from within nautilis, add content and save them. I can also create new folders and files from the right click menu. but dragging files from another location, or the same location (creating a copy), results in the afore mentioned error.

On another machine running ubuntu intrepid, I've been able to do this for quite some time, so it seems as this is a new bug.

Travis

---

### Post by zigx on 2009-03-23
have you guys found a workaround?

---

