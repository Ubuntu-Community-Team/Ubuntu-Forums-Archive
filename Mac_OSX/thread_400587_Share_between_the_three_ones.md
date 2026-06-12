---
title: "Share between the three ones"
date: 2007-04-03
forum: Mac OSX
---

### Post by oskarloko on 2007-04-03
I've a triple boot macbook - two for play, one for all.

I would like to make a share-data partition.

I've used ext3 with [win]("http://www.fs-driver.org/") and [osx]("http://sourceforge.net/projects/ext2fsx") drivers. 
But osx are buggy and doesn't work rigth

I was thinking on using vfat - but I don't know how to mount it on OsX...


¿ Is there any other fs accesible to three OS ?

---

### Post by oskarloko on 2007-04-03
mmm.. i didn't notice about that


Using HFS+ between OsX and Linux
Using ext3 between Linux and Xp 

[http://ubuntuforums.org/showthread.php?t=396125&page=2](http://ubuntuforums.org/showthread.php?t=396125&page=2)

It's a little experimental... may work


But not one partition to share for them all...

---

### Post by oskarloko on 2007-04-10
Well, just using (into console on $HOME dir )

```

sudo mount_msdos /dev/disk0s6 /data
ln -s /data Data

```

and it works on OsX

I'll seek how to automount at init

On linux is only (into console on $HOME dir )
```

sudo mount /dev/sda6 /data
ln -s /data Data

``` 

I've to see about permissions, but on OsX I can use new partition without problems

( as it is more than a 4th primary partition, Win can't see it... but if it were beyond It would work )

---

### Post by 3rdalbum on 2007-04-10
Fat32 can be read and written on the Mac OS. HFS can be reliably written on OS X and Linux, and I believe there is a driver for WIndows. It may be shareware/commercial though.

---

### Post by oskarloko on 2007-04-11
Well, I saw this

and added my two cents

[http://forum.insanelymac.com/index.php?showtopic=23056&st=0&gopid=345127](http://forum.insanelymac.com/index.php?showtopic=23056&st=0&gopid=345127)

For the Redmon os
[http://www.f.kth.se/~f96-bet/hfsutils/](http://www.f.kth.se/~f96-bet/hfsutils/)
and with some money
[http://www.mediafour.com/products/macdrive/](http://www.mediafour.com/products/macdrive/)
( too much privative OS to be free, I'm afraid )

However, I'll looking foward a stable ext3 driver for OsX


Thanks !!

---

