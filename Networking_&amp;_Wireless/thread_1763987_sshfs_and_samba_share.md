---
title: "sshfs and samba share"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by Azyx on 2011-05-21
I have an ubuntu 10.04lts as server and 2 problems and ione of them can solve it.
[COLOR=Red]
How to get read-only with sshfs?[/COLOR]
I want to share some files (mostly music) to the rest of my computers. sshfs mounts the shared foldders nicly and I looks as it the computers own filesystem. How can I mount the read-only with sshfs?

[COLOR=Red]How to mount samba as a file system?[/COLOR]
Another option is samba. But I am not able to mount them as a folder and the music player can't reach them from inside, cos they are network.folders: Using clementine music player but other file browser players have the same problem.

cheers

---

### Post by Morbius1 on 2011-05-21
> [COLOR=Red]How to mount samba as a file system?[/COLOR]
Another option is samba. But I am not able to mount them as a folder and  the music player can't reach them from inside, cos they are  network.folders: That's two different problems. How are you mounting the folder?

If you browse to the remote folder using Nautilus or Network then the remote share is mounted at :
> /home/username/.gvfs/sharename on servernameYou will need to enable "show hidden files" in Nautilus or pcmanfm and your application to access the mount point.

If you are accessing the remote share with a mount command then post it so others can see how you are doing it.

---

### Post by Azyx on 2011-05-21
> **Morbius1 said:**
> That's two different problems. How are you mounting the folder?

If you browse to the remote folder using Nautilus or Network then the remote share is mounted at :
You will need to enable "show hidden files" in Nautilus or pcmanfm and your application to access the mount point.

If you are accessing the remote share with a mount command then post it so others can see how you are doing it.

Ok. no I just mount by browse in Places-->Network-->computernane. will see if it work. /cheers.

---

### Post by Azyx on 2011-05-21
> **Morbius1 said:**
> That's two different problems. How are you mounting the folder?

If you browse to the remote folder using Nautilus or Network then the remote share is mounted at :
You will need to enable "show hidden files" in Nautilus or pcmanfm and your application to access the mount point.

If you are accessing the remote share with a mount command then post it so others can see how you are doing it.

Thax it works I the media player are able to brows after hidden files. Is the mabe a possibility to link to a visible folder on the desktop?

---

### Post by Morbius1 on 2011-05-21
You can try a symbolic link:

```
ln -s /home/username/.gvfs/"sharename on servername" /home/username/Desktop
```Don't forget the " " around the sharename on servername because of the spaces.

---

### Post by Azyx on 2011-05-24
> **Morbius1 said:**
> You can try a symbolic link:

```
ln -s /home/username/.gvfs/"sharename on servername" /home/username/Desktop
```Don't forget the " " around the sharename on servername because of the spaces.

Thans. will try it.

---

### Post by Azyx on 2011-05-26
> **Azyx said:**
> [COLOR=Red]
How to get read-only with sshfs?[/COLOR]
I want to share some files (mostly music) to the rest of my computers. sshfs mounts the shared foldders nicly and I looks as it the computers own filesystem. How can I mount the read-only with sshfs?
cheers

..so simple. just add **-o ro** :)

---

