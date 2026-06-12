---
title: "New NFS issue - not present in V11.10 or earlier"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by hawthorne on 2012-05-03
I just reinstalled my kids system with Xubuntu 12.04 and hit an NFS issue that I didn't have with earlier Ubuntu/Xubuntu's.

I'm exporting her home directories from a server (192.168.1.30) to her client machines. 

On the server, the /etc/exports file contains:

/srv/lauren 	192.168.1.51(rw)

This is the correct address of the client system.


On the client, the fstab entry is:

192.168.1.30:/srv/lauren 	/home/lauren	nfs 	defaults 0 	0 

The result is that the Desktop shows NONE of the files in the Desktop folder on the server, BUT you can still use filemanager to read them!!

'df' on the client now shows:

gvfs-fuse-daemon          66649856 18586240  44677888  30% /home/lauren/.gvfs
192.168.1.30:/srv/lauren  66649856 18586240  44677888  30% /home/lauren

ALL files are visible in their specific directories.
Previously only the 'nfs' live was present.

QUESTIONS:
i) Why doesn't the desktop display properly anymore on the client machine; it used to on 11.04 ?:confused:


ii) Is there a fix & what is it?

Thanks in advance for your help/comments

Hawthorne

---

### Post by hawthorne on 2012-05-03
Solved:

Don't know if this is an approved way, but it worked :)

i) Renamed .gvfs directory to .gvfs2
ii) Logout & login, .gvfs directory recreated automatically, everything was back to as before and working
iii) Remove .gvfs2 directory 


Go get coffee:D

---

