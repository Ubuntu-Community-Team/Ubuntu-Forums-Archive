---
title: "gtkPod not Working!"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by Aifel on 2007-01-16
Hello everyone. So, my gtkpod isn't able to write songs to my iPod, or delete songs off of it. When I try to sync changes, it gives me an error (error shown below). Has anyone else had this error, and if so, has anyone fixed it?

When trying to delete songs:
```
Some tracks could not be deleted from the iPod. Aborted!
```


When trying to ADD songs:
```
Error opening '/media/ipod/iPod_Control/Music/F12/gtkpod301868.mp3' for writing (Read-only file system).

Error opening '/media/ipod/iPod_Control/Music/F13/gtkpod235178.mp3' for writing (Read-only file system).

Error opening '/media/ipod/iPod_Control/Music/F14/gtkpod117067.mp3' for writing (Read-only file system).

```

---

### Post by lukew on 2007-01-16
> **Aifel said:**
> Hello everyone. So, my gtkpod isn't able to write songs to my iPod, or delete songs off of it. When I try to sync changes, it gives me an error (error shown below). Has anyone else had this error, and if so, has anyone fixed it?

When trying to delete songs:
```
Some tracks could not be deleted from the iPod. Aborted!
```


When trying to ADD songs:
```
Error opening '/media/ipod/iPod_Control/Music/F12/gtkpod301868.mp3' for writing (Read-only file system).

Error opening '/media/ipod/iPod_Control/Music/F13/gtkpod235178.mp3' for writing (Read-only file system).

Error opening '/media/ipod/iPod_Control/Music/F14/gtkpod117067.mp3' for writing (Read-only file system).

```

It has been mounted as readonly. Maybecause the mount options were specified as that, maybe because it turned readonly.

Do a fsck to ensure everything is ok.

I had to recreate my dbf file before it would work for me. I read somewhere that you either do it linux or windows but not both....

Let us know how you get on.

Luke

---

### Post by Aifel on 2007-01-16
Im kinda a Linux newb, so when I put in fsck, it says I may damage my file system. Should I continue, and should I have my iPod mounted already when I run fsck?

---

### Post by lukew on 2007-01-17
> **Aifel said:**
> Im kinda a Linux newb, so when I put in fsck, it says I may damage my file system. Should I continue, and should I have my iPod mounted already when I run fsck?

You should unmount your ipod first and then fsck it!

You should never fsck a mounted drive. It drives me crazy when you see people giving this advice. The only drive you should check when mounted is /, and then you should init 2!

Let us know how you get on.

Luke

---

### Post by nevin on 2007-01-25
im having this same problem... but i dont know what to do with fsck....
i unmounted my external and my ipod, and then it gave me

```
nevin@italia:~$ fsck
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/dev/sda2 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?
```


/dev/sda2 is my ubuntu system... so i dont know what i should do about that....

---

