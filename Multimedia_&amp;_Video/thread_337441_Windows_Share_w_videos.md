---
title: "Windows Share w/ videos"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by FrostyFlames on 2007-01-13
Hello,
Currently I am trying to play a video off a windows share(I gave myself full rights to the folder) that I have connected to through my Ubuntu client. If I copy the video file to my desktop and open it with VLC, it works just fine and the video will play. But if I right click the file, or double click, on the shared drive VLC opens and just does nothing as if I had just opened it. I am wondering if I am doing something wrong, or I havn't set some weird setting. ](*,)

PS: I have no idea if this should have gone here or in the network section

---

### Post by dbd on 2007-01-13
Strange, have you tried playing it with any other media players?

---

### Post by pete on 2007-01-13
From the "connected to through my Ubuntu client" part, I'm assuming that you used the "Connect to Server" wizard off the Places menu to get to the Windows share.

The problem you're having is due to the fact that VLC doesn't understand how to get to an SMB share that isn't mounted in your local filesystem.  

You'll need to mount the Windows share locally.  You can do this on a one-time basis with the mount command in terminal, or add the Windows share to /etc/fstab to mount it automatically on startup.  There's a pretty good write-up of the process here [https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28mount%29](https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28mount%29)

---

