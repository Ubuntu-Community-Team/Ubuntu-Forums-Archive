---
title: "How about NFS"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by RRahl on 2010-06-23
Alright so far help has been limited, I have tried Samba and iSCSI but neither topic has gotten me much help so I figure I can try NFS.
So far I have attempted to set up NFS on ubuntu 9 and am running into a wall.
Here are the steps I have done so far:
sudo apt-get install nfs-kernel-server
sudo nano /etc/exports
added the line "/home/user/Desktop/debian 192.168.20.43(rw,no_root_squash,async)"
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a
I head over to my windows 7 (192.168.20.43) box and install nfs services and run the following command:
mount \\Odin9:/home/user/Desktop/debian *
and I get Network Error - 53 (The network path was not found)
Yes I can ping Odin9

I have used the following resources in troubleshooting
[http://ubuntuforums.org/showthread.php?t=310168](http://ubuntuforums.org/showthread.php?t=310168)
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

At the end of the day, all I want is a share on Ubuntu that is accessible from my windows 7 network...been working on this for 2 weeks to no avail.

---

