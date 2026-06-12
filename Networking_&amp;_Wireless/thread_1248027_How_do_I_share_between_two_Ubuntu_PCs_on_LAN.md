---
title: "How do I share between two Ubuntu PCs on LAN"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by slugicide on 2009-08-23
I don't know how to share folders between two Linux machines. I would think that when I went to "Network" it would show me the Linux computers on the LAN, but it just says "Windows Network" and I get an error when I try to open that. (There's a third Windows machine that doesn't show up here, either.)

When I right click a folder and choose "share" it doesn't make a difference on the network. As in: I still can't see either PC.

---

### Post by wojox on 2009-08-23
You'll want to install openssh on each computer.

```
sudo apt-get install openssh-client openssh-server
```

Then in a terminal:

```
ssh remoteuser@remotebox
```

Graphically open Places > Connect to Server and pick ssh

---

### Post by slugicide on 2009-08-23
Thanks for the quick reply, Yoda. Question: is this an all terminal solution? Because I don't think I can teach my mother things like cd and pwd. I can barely move around in the thing. Thanks!

---

### Post by wojox on 2009-08-23
No you can go to Places > Connect To Server
Pick SSH and login.
Everything will be graphical.

As far as installing it graphically open synaptic and search ssh.

---

### Post by slugicide on 2009-08-23
This solution isn't really working because not only can I not do this (I have no idea what to type in the "server" field), I could never explain to my mother or anyone else how to do it, either. 

As far as I know if you have two Windows computers or two Macs it's dead simple to drag and drop files between them without having to be a network engineer (I've done it on Windows many times). 

Is there really no simple way to share files over a network among two Ubuntu computers?

---

### Post by The Foz on 2009-08-24
Of course there is an easy way to share files between computers, and to have WYSIWYG access to them.

I think that the reason you didn't get the answer you expected earlier, is that you didn't say what you wanted to share.

Basically, to share files, there is a share manager. The default in 9.04 is to share using Windows file sharing protocols, so you just have to give the share a unique name. You need to have Samba installed first. If you want to be able to write as well as read, you will probably need to "allow others to write/update".

The procedure is that you share the files on the computer where the files are physically stored, and then mount them (make them visible) on the other computer(s). To set up mounts that are permanent, you will need to add one or more lines (one for each share that you want mounted) in the file /etc/fstab. After editing the file, type 'sudo mount -a' and they will be mounted. make sure that you keep a backup copy (e.g. /etc/fstab.orig) of the fstab file before you start editing.

---

### Post by superprash2003 on 2009-08-24
take a look at this as well [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by slugicide on 2009-08-24
*sigh* Thanks for your help everybody. I hope someday Ubuntu computers will network with each other "out of the box."

---

