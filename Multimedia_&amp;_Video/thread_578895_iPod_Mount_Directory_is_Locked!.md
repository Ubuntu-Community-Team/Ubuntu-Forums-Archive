---
title: "iPod Mount Directory is Locked!"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by umechanism on 2007-10-17
I've been switching between Amarok and gtkpod for syncing my 5th gen. video iPod.  During the last syncing with Amarok, I pulled the usb cable out before selecting "Disconnect".  Now, I can't make the iPod mount anymore.  Oddly, the mount directory is LOCKED.  I can view it with Konqueror (KDE) and it actually shows a picture of a lock on top of the file. When selected, it tells me that I do not have permission to view the file.

Amarok has sense created another Ipod mount "Ipod-1".  

How can I fix this.  I need to get back to the original mount point and get Amarok to sync again.

Please Help.

M

KDE
Feisty 7.04

---

### Post by anthonyJC on 2007-10-18
i think i've seen this before on my brothers  set-up -dont use ipods myself. i think gtkpod changes ownership of the mount point to root.root. you need to open a konsole and copy paste this is in (after editing in your name):

sudo chown yourusername.root //media/ipod; chmod 770 //media/ipod

that gives u a permament fix since ipod folder is not deleted.  so this is preferred.

so if your name is john it is 
sudo chown john.root //media/ipod; chmod 770 //media/ipod


or just, for a temporary fix - should get it back to before it went wrong but can go wrong again

sudo rmdir //media/ipod

---

### Post by umechanism on 2007-10-18
Oddly, the folder is now unlocked and seems to be working correctly now.  I'll bookmark this thread and try your suggestion should it lock again.

Thanks for the response.

M

---

