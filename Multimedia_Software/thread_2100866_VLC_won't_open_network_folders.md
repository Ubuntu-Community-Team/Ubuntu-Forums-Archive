---
title: "VLC won't open network folders"
date: 2013-01-03
forum: Multimedia Software
---

### Post by Stonecold1995 on 2013-01-03
Because I use a laptop, I have limited hard drive space, so I store most of my music on another computer in my local network.  But I'd like to be able to access that music wirelessly with VLC as a playlist, however it seems that VLC refuses to open remote *folders*, and will only play one remote *file* at a time.  Is there a way to bypass this seemingly arbitrary limitation and play remote folders in a playlist?  I use the fish protocol to connect to remote drives.

The current work-around I have is to mount the remote folder with sshfs, but that is very slow (it actually mounts the remote folder, so Dolphin will see it as a local file system and subject it to all the I/O intensive features available to a true local file system, such as loading thumbnails or generating previews for large files, going recursively into folders to preload file size, etc).

---

### Post by Stonecold1995 on 2013-01-09
bump

---

