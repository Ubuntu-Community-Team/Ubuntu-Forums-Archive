---
title: "HELP! problem with r/w access:"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by dbpbandit on 2010-01-22
Hey All, I installed a Netgear ReadyNAS 2100 on my network and everything works fine upfront but I'm having a couple of issues and I hope someone here can help me. 

When I first brows the network, (using Nautilus 2.26.2/ubuntu 9.04/gnome) I can locate the NAS and go to the share folder - everything works fine BUT after a few times using (copy past/new folder/etc) I lose my ability (r/w access) to write to the share. If I try to create a new folder or even past a file it gives me an error and says I don't have permissions to do that. So I figured I would try to mount the drive via terminal  but I cant even manage to do that. I keep getting a "mount error(13) Permissions denied" message.

sudo mount //192.168.***.***/sharename -o username=domain\username,password=**** /mnt/install
mount error(13): Permission denied
Refer to the mount.cifs(8 manual page (e.g.man mount.cifs)

 Am I doing this correctly? Is there a different terminal command I should be using?

So far the only way I can get read/write permissions to work again is to reboot. I also have the same exact issues on my laptop, also running the same versions of ubuntu,nautilus,gnome so it's not an issue with my desktop it must be something else. Any suggestions? Thanks.

-Dave

---

### Post by dbpbandit on 2010-01-22
Bump????

---

### Post by dbpbandit on 2010-01-25
BUMP x 2???

---

### Post by chmmr on 2010-04-23
This may not be exactly the issue you're seeing, but just in case:

[http://ubuntuforums.org/showthread.php?t=1369040](http://ubuntuforums.org/showthread.php?t=1369040)

---

