---
title: "set up dataless workstation?"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by jimmybarcelona on 2009-09-08
Never done anything quite like this before, need to know the best way to go about it. I have a rack server running jaunty server edition and 3 computers I would like to set up as dataless workstations. Currently they have jaunty desktop edition on them. I would like it so that when a user logs on the system automatically mounts their home folder from the server rather than the local machine. 

To do this would I simply change the user's $home variable on each workstation to point to their homefolder as an nfs or sshfs share on the server? Or should I leave the default home folder on the local workstation as is and simply add a script to run at startup that automounts their home folder on the network to their homefolder on the local machine? Or is there a 3rd option that I'm unaware of? 
Thanks much!

---

### Post by i.r.id10t on 2009-09-08
I'd have all /home directories come off the NFS server... 

So login to the machines, move /home to /oldhome or similar, re-create /home and add mount point in /etc/fstab.  If you want to be nice about it, copy the contents of the /oldhome to the NFS share :)

---

### Post by finite9 on 2009-09-17
what if you want to mount your home directory from a laptop where networkmanager does not come up until after login?

I would really like to know how to do this.

Also, could you script in a bypass so that when you are away from home network, it does not error on login?

---

### Post by jimmybarcelona on 2009-09-18
The way I finally ended up going was to use nfs. I edited the fstab file to automatically mount the home folder from the remote system to /home mount point on the local system. This might work for you finite9 without using a script at all. If the entry in the fstab file is unavailable (i.e. you aren't at your home network) it just ignores the line saying to found the remote nfs system and the local /home folder is used instead. the trick would be getting at the things on your local home folder when the machine boots within range of your home network and automatically mounts the remote home folder. but you should be able to do that with sudo umount.

---

