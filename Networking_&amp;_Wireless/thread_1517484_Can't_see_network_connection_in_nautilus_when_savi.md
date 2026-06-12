---
title: "Can't see network connection in nautilus when saving or opening files with programs."
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by AfrikaDietmar on 2010-06-25
Hi,

i recently migrated from windows to ubuntu 10.04 and managed after weeks of research, trial and error, and learning from this forum to get it to work. This place is a great ressource and also thanks to all those who helped me before.

I run a samba network with ubuntu machines only. 
Everything works fine there. I don't use nautilus sharing.

In Nautilus file browser 2.30.1 I can see under places in the left the Network folder which is mountable and i can access the server in this way. Here as well everything is ok.

We store all our files on that server and the idea is also to access them all from there.
What i have noticed though is that when we try to save a document with open office we don't get the network option to choose when the natilus browser pops up asking where to save the file.

Likewise when i need to add files in a web browser to send them to a client i also do not get the network link function under places in nautilus. Can this be made ? I've attached a screenshot.

Do you have an idea how this mountable network link can also be placed in that nautilus file browser ?

Greetings from tropical africa!! :)

---

### Post by AfrikaDietmar on 2010-06-25
I found a solution.

Well 2 solutions, i kind of pulled the mounted server connection i had on my desktop into nautilus under places and when i rebooted my machine, when i save files with certain programs i kind of sometimes see that connection, but not with all programs. Not very clean way.

The best way is to use GVFS to mount point the access to files in the network  folders from applications that don't accept smb:// paths.

For example, to browse mounted network folders in those programs, enter  /home/<username>/.gvfs/

I use nautilus, activate show hidden folders, then go to .gvfs and there i see all my network folders.

This post also helped me:
[http://ubuntuforums.org/showthread.php?t=1383206](http://ubuntuforums.org/showthread.php?t=1383206)

---

