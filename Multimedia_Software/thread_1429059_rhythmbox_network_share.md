---
title: "rhythmbox network share"
date: 2010-03-13
forum: Multimedia Software
---

### Post by baddnady23 on 2010-03-13
I have all my music on another computer on the local network at my place.  When playing it through rhythmbox, it works great except for one thing.  If I want to click on the tracking status bar thing that shows how far into the song you are so that I can skip to a spot further into the song, it won't let me.  However, when I play music that is stored on the computer with rhythmbox, your able to.  Is this a bug or do I have a setting not right?  I have the network buffer set to the max, 1024 but it hasn't done anything...

---

### Post by baddnady23 on 2010-03-14
bumbity bump bump

---

### Post by vanadium on 2010-03-15
This is probably related to the way your share is connected.

---

### Post by baddnady23 on 2010-03-20
How so? It is set up over SSH...

---

### Post by vanadium on 2010-03-21
You might need an nfs mount or a samba mount for this to work properly. ssh essentially is some kind of a file transfer protocol, and probably does not in all aspects behave as a local file system.

---

### Post by baddnady23 on 2010-03-24
Thank you.  I mounted the drive using samba and it seems to be working great now.  Now I just need to learn the ins and outs of samba configuration.

---

### Post by SoFl W on 2010-05-21
Interesting...  I can not get this to work.  What are your share or file permissions for the music folder?  (Are you using a folder or a drive?)

I can play the files using other applications but Rhythmbox will not import or recognize the files on the shared drive.  The only thing I can think is that Rhythbox sees they are read only?

---

### Post by baddnady23 on 2010-06-06
> **SoFl W said:**
> Interesting...  I can not get this to work.  What are your share or file permissions for the music folder?  (Are you using a folder or a drive?)

I can play the files using other applications but Rhythmbox will not import or recognize the files on the shared drive.  The only thing I can think is that Rhythbox sees they are read only?

What I ended up doing actually was setting a NFS between to the two computers so that I could mount the drive on the client computer and it worked perfectly. :)

---

