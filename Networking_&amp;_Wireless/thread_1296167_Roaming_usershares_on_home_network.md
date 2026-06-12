---
title: "Roaming usershares on home network"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by Dr_Hugh on 2009-10-20
Hello all,

I am trying to set up an Ubuntu file server for a home network using Intrepid desktop on the server and clients. On the network are three Ubuntu clients and two Windows clients. The Ubuntu clients can be used by any members of the family but would like to keep their files private.The Windows boxes are used only by their owners.

Using cifs so the share will be available from Windows and Ubuntu I am at the happy state where Bill can log onto a linux client and his server share appears on the desktop.

The problem is how to enable this for the other users and I have looked through many posts to find the answer.

The users all have accounts with the same UID and GID on all of the systems.

Can anyone point me in the right direction?

Thanks in advance.

---

### Post by Dr_Hugh on 2009-11-02
After a bit of a struggle I have achieved what I needed. It is not the neatest system and I am not sure how secure it is.

I set up Samba to share the users home directories using a separate password file for each user in their home directory on the server. 

On the client machines I used fstab to mount all of the users home directories to /mnt/user.
 
Logging onto the system as the user I created symlinks to the directories in /mnt/user/ that I wanted on the desktop.

So now when Bill logs on to any client he has access to his own files from the server and if Jill logs on she has her own files.:D

I have only sketched out a brief outline, if you get stuck I will elaborate.

If anyone has any better ideas please join in ;)

---

