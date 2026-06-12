---
title: "nfs and streaming?"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by Leoooo on 2010-03-15
Hi, I have a nfs question.
How is nfs with mounts?
 
I'm trying to stream content from my ubuntu box to my mediaplayer (popcorn hour).
 
 
My structure is like this:
 
/media   <- sda
/media/pictures   <-sdb
/media/tournaments   <-sdc
 
When I add the media share through nfs, everything seems to work, and I can enter the subdirs.
 
But when I enter dirs that are mounted, e.g. pictures, I get 'no content found'.
 
Is this a nfs issue or media player related?

---

### Post by suseendran.rengabashyam on 2010-03-15
Hi,

In your NFS server, I guess your /etc/exports file might look like this:

```
/media xxx.xxx.xx.xx(rw,sync,no_subtree_check)
```

make sure that you add the following two lines

```
/media/pictures xxx.xxx.xx.xx(rw,sync,no_subtree_check)
```

```
/media/tournaments xxx.xxx.xx.xx(rw,sync,no_subtree_check)
```

In your NFS client add the following lines to the /etc/fstab file

```
xxx.xxx.xx.xx:/media /media nfs rw,hard,intr 0 0
```

```
xxx.xxx.xx.xx:/media/pictures /media/pictures nfs rw,hard,intr 0 0
```

```
xxx.xxx.xx.xx:/media/tournaments /media/tournaments nfs rw,hard,intr 0 0
```

Make relevant changes to the above lines to suit your environment.

Hope this helps.

---

### Post by Leoooo on 2010-03-15
It's a mediaplayer.

So there is no fstab.

But I tried to add the shares, and still the same as before.

---

### Post by Leoooo on 2010-03-16
No nfs experts here??
 
I can't be the only one who wants to share a folder, where there are several hdd's mounted ???

---

### Post by suseendran.rengabashyam on 2010-03-16
Hi,

Did you execute the following command

sudo /etc/init.d/nfs-kernel-server restart

after making changes to your /etc/exports file ?

---

### Post by Leoooo on 2010-03-17
Yes. And rebooted.
 
The 'pictures' and 'tournaments' shares work seperatly, but just not from /media :/

---

### Post by suseendran.rengabashyam on 2010-03-17
Hi,

In /etc/exports file do the following

1) Include the 'fsid=0' option in the following line
```
/media xxx.xxx.xx.xx(rw,sync,no_subtree_check)
```
i.e
```
/media xxx.xxx.xx.xx(rw,sync,no_subtree_check,fsid=0)
```


2) Include the 'nohide' option in the following two lines

```
/media/pictures xxx.xxx.xx.xx(rw,sync,no_subtree_check)
```
```
/media/tournaments xxx.xxx.xx.xx(rw,sync,no_subtree_check)
```
i.e
```
/media/pictures xxx.xxx.xx.xx(rw,sync,no_subtree_check,nohide)
```
```
/media/tournaments xxx.xxx.xx.xx(rw,sync,no_subtree_check,nohide)
```

After making the changes restart the nfs-kernel-server 
```
sudo /etc/init.d/nfs-kernel-server restart
```
More details can be found in this thread
[http://ubuntuforums.org/showthread.php?t=710339](http://ubuntuforums.org/showthread.php?t=710339)

Hope this helps.

---

### Post by Leoooo on 2010-03-17
Thanks alot.

That fixed the problem :D

---

