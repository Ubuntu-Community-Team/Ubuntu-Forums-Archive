---
title: "How to add a network library in amarok?"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by Boomy on 2007-11-05
I'd like to add the music folder on my desktop to my laptop using Amarok but I don't see how to accomplish this. Does anyone know, or know a music player that will let me do this? Thanks

---

### Post by michaelzap on 2007-11-05
> **Boomy said:**
> I'd like to add the music folder on my desktop to my laptop using Amarok but I don't see how to accomplish this. Does anyone know, or know a music player that will let me do this? Thanks

Just share the folder with music on your desktop and mount it on your laptop (give it a mount point). Then you can add it to Amarok or whatever other music program you prefer. I have my music library on a networked Samba server and Amarok plays it just as if it were a local library.

---

### Post by Boomy on 2007-11-06
I have the folder shared, but when I go to import a folder in amarok it only shows local folders, no shares. When I try to drag and drop from the share, amarok won't play it, I assume because the path in amarok is an "smb://user@....." path. I can drag it to my desktop then drag to amarok and it plays fine.

---

### Post by michaelzap on 2007-11-06
> **Boomy said:**
> I have the folder shared, but when I go to import a folder in amarok it only shows local folders, no shares. When I try to drag and drop from the share, amarok won't play it, I assume because the path in amarok is an "smb://user@....." path. I can drag it to my desktop then drag to amarok and it plays fine.

You need to set a mount point for the shared directory, an dthen you'll be able to access it at /mnt/whatever instead of smb://user@whatever.

---

### Post by Boomy on 2007-11-06
I didn't know I could do that! I've always connected through the gui.  What is the syntax to mounting a share on a server?  I tried "mount /servername/sharename media/mountedshare" but it didn't work.Thanks in advance.

---

### Post by michaelzap on 2007-11-06
Well if you're going to be using this share consistently in Amarok you should probably add it to your fstab file so that it's mounted on every boot. There are a lot of tutorials out there and posts here in the forums for doing this, but basically you create an empty folder in the mnt directory (you need to be sudo to do this) which will serve as your mount point (e.g., "music"). Then you add a lint to the fstab file (which you also need to edit as root) with something like:

//server-name/share-name /mnt/music cifs

I've had better luck with cifs than samba in Gutsy, but you should be able to do it either way. If the share requires a username and password to connect there are a couple ways that you can have those entered automatically. Search the documentation for more specifics.

After you've edited your fstab file, you can mount all of the drives listed in there without rebooting by typing sudo mount -a in a terminal window.

---

### Post by peitschie on 2007-11-06
This link might also help:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

---

### Post by Boomy on 2007-11-06
Excellent. Thanks for the help :)

---

