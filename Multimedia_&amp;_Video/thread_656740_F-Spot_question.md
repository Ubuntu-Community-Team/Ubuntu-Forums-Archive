---
title: "F-Spot question"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by tato97 on 2008-01-02
Sorry this might be a stupid question but I'm new to Ubuntu...learning everyday.

I have my photos stored in an external drive connected to a Vista machine.  I have managed to mount that drive into my Ubuntu 'desktop' it shows as My Book with a SMB connection. I can surf to that drive and view/open pictures. 

My question is, can I get F-Stop to view that location where the pictures are w/o re-copying them to the Ubuntu machine? I managed to do something similar with my music using Rhythmbox but can't figure out how to do it with the pictures.

I can't find anywhere in F-Stop that mounted drive...? It seems it only looks at local folders in the Ubuntu machine and there is no way to look for pictures on the network.

Any help is appreciated!

Thanks

---

### Post by A*p on 2008-06-12
You may be able to set up a Symbolic link to the networked directory, or make it a mount point. I have no vista and do not use F-spot and cannot try it myself, so just a suggestion.

---

### Post by eldragon on 2008-06-12
> **A*p said:**
> You may be able to set up a Symbolic link to the networked directory, or make it a mount point. I have no vista and do not use F-spot and cannot try it myself, so just a suggestion.

symlinks are for files, not folders.

are you mounting the share through fstab?
if so, you could bind that mountpoint to some other mount point in the Pictures folder in your home.

make f-spot scan for media :D

---

