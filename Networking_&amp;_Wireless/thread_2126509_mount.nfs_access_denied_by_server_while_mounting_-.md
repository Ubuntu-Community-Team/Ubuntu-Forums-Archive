---
title: "mount.nfs: access denied by server while mounting - once more..."
date: 2013-03-17
forum: Networking &amp; Wireless
---

### Post by Eunegis on 2013-03-17
Hi Experts,

I'm having the above problem. Obviously its an individual version of it since no recepie I could find on the internet can solve it.
I'm trying to automount two directories on a Synology DS212 to my Kubuntu 13.04beta-1 system. But the version doesn't matter: its the same problem under Kubuntu 12.04.2 and OpenSuse 12.3.
While I'm following this recepie:
"[http://www.markinthedark.nl/news/ubuntu-linux-unix/85-howto-mount-synology-nas-ds211j-to-ubuntu.html](http://www.markinthedark.nl/news/ubuntu-linux-unix/85-howto-mount-synology-nas-ds211j-to-ubuntu.html)" 
I get the output after "sudo mount -a" (e.g.): "mount.nfs: access denied by server while mounting 192.168.178.22:/volume1/Hires".
It looks to me like some hickup occuring on the NAS' side, but I'm not sure. I tried several fstab options, but nothing ever changes. I removed the NAS' password as well - without effect.
If I try to click on the NAS directories in Dolphin (which were created by saving the changes in the fstab) it answers:
"An error occurred while accessing 'personal folder', the system responded: mount: only root can mount 192.168.178.22:/volume1/Hires in /home/hires".
Browser access to the Synology works fine. But I can't mount anything natively inside Kubuntu.

My fstab looks like this:
_____
[...]
#
192.168.178.22:/volume1/Mucke /home/mucke nfs nouser,atime,auto,rw,dev,exec,nosuid 0 0
192.168.178.22:/volume1/Hires /home/hires nfs nouser,atime,auto,rw,dev,exec,nosuid 0 0
_____

Where am I going wrong???
I admit that I'm far from being an "insider" concerning Linux. But does it have to be so rotten complicated to mount a simple NAS/folder in a Linux system in the year 2013? Haven't we gotten any further yet? By the way: the OpenSuse installation through YAST offers an automount integration of network drives during the installation process (which ubuntu doesn't), but even that option is useless: test mounting by YAST constantly fails in my case.

Thanks in advance for your help.
Regards,
Eunegis

---

### Post by Eunegis on 2013-03-17
OK, let me talk to myself just a little...

Could it be that the following information from inside the terminal during nfs-common install should be used somewhere somehow?:
_____
[...]
Creating config file /etc/default/nfs-common with new version
Create systemuser »statd« (UID 113) ...
Create new user »statd« (UID 113) with group »nogroup« ...
Do NOT create home directory »/var/lib/nfs«.
[...]
_____

Thanks,
E

---

### Post by SeijiSensei on 2013-03-17
It's a problem with permissions on the server side.  Can you view any logs on the device?  Does it allow you to set NFS options?  If so, try enabling "no_root_squash" and see if that helps.

---

### Post by Eunegis on 2013-03-17
Well...

Thanks Seiji. Meanwhile I found the "trick".
Its a little embarassing actually, but on the other hand not a single post anywhere on the internet emphasized it:
in the NFS privileges of the shared folders on the NAS the hostname or IP has to be the one of the client (the Ubuntu machine), not the NAS (which is in fact the server). 
Once I had found out about it things appeared perfectly logical. But after it all you're always a tad smarter than before. Experts know about it right away, but not newbies like me - especially if one's point of view is that computers shall serve the user, not the other way around (like in my case). Ubuntu has advanced a lot during the passed few years, but do things like that still have to be so awkward? Isn't it possible to have a little self-explaining GUI for an action that is so common nowadays?

E.

---

### Post by SeijiSensei on 2013-03-19
Why is this Ubuntu's "fault?"  All NFS servers enforce security by, among other means, limiting the range of client IP addresses that they will allow to mount.  Your NAS box is just following the NFS standards.

---

