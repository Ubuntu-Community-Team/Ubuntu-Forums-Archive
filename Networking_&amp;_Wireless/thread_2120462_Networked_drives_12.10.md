---
title: "Networked drives 12.10"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by emacdonald on 2013-02-26
I have a NAS drive with a number of NFS shares on it. These have been mapped to the Main 12.10 machines via fstab etc... Everything works fine, apart from when the 12.10 machines boot up, they insist on opening up all shared network drives in Nautilus windows. (This did not happen on earlier distros) & (There are no tasks in the Startup Applications.)
I checked by booting up with old 10.04 configured drive,(with the same NFS/fstab config on it) and it seemed to be fine. Any ideas?

---

### Post by redmk2 on 2013-02-26
> **emacdonald said:**
> I have a NAS drive with a number of NFS shares on it. These have been mapped to the Main 12.10 machines via fstab etc... Everything works fine, apart from when the 12.10 machines boot up, they insist on opening up all shared network drives in Nautilus windows. (This did not happen on earlier distros) & (There are no tasks in the Startup Applications.)
I checked by booting up with old 10.04 configured drive,(with the same NFS/fstab config on it) and it seemed to be fine. Any ideas?

Where are the NFS exports mounted on the 12.10 machines?  Post the contents of the /etc/fstab file so we can see what you are talking about.

---

### Post by emacdonald on 2013-02-26
192.168.1.74:/Documents /home/office/NAS_Documents nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Music /home/office/NAS_Music nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Photos /home/office/NAS_Photos nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Videos /home/office/NAS_Videos nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Media /home/office/NAS_Media nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

With Directories created in /home/office for each of the items above. e.g NAS_Documents

---

### Post by redmk2 on 2013-02-26
> **emacdonald said:**
> 192.168.1.74:/Documents /home/office/NAS_Documents nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Music /home/office/NAS_Music nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Photos /home/office/NAS_Photos nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Videos /home/office/NAS_Videos nfs rsize=8192,wsize=8192,timeo=14,intr 0 0
192.168.1.74:/Media /home/office/NAS_Media nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

With Directories created in /home/office for each of the items above. e.g NAS_Documents

Not what I expected.  The fstab entries seem fine to me.  I thought maybe you had mounted these at /media/<somesuch>.  This would have made them showup automatically.

What happens if you unmount an export and then mount it manually (sudo mount -t nfs etc)?  Does it reappear when you mount it manually?

[COLOR="Blue"]**Edit:** I just tried what I recommended to you.  If I mount the exports in my home directory (something I never do), they show up on my desktop.  If I mount them as I usually do at /data they do not show up.

My recommendation is to mount you exports *outside *of the home directory tree.  I use /data for all of my NFS mounts but you could create /nfs or use /srv just as easily.  You should set the group ownership to the group *users* and make sure you are added to that group.

The bottom line is:  The home directory is not for anything or anybody from the outside,  If you must access these through your home directory you can create a sym-link or mount the /data directory using *mount bind*.  I never do.  I just use the /data dir directly.[/COLOR]

---

### Post by emacdonald on 2013-02-27
Ok Thanks for that. will have a go when i get back to the machine at the weekend.

---

