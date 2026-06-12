---
title: "Arch, Myyhtbuntu samba permission problems"
date: 2009-08-17
forum: Mythbuntu
---

### Post by DigitalDuality on 2009-08-17
I have 2 machines in my house that have samba shares on them(Mythbuntu boxes). 

And I have an Arch desktop,  if i access the Mythbuntu shares, when mounting they prompt me for a password.  If i enter the only user/sudo password on box1 it'll allow me to mount one of them, but not the other.  On box2 it doesn't seem to matter what I enter.  This whole requiring a password thing, doesn't happen on another boxes (Ubuntu, Suse, Gentoo, windows, etc).

Permissions on making directories is wierd too.  I can make a directory, but upon making it I do not have permission to delete it, put anything within it, etc... its as if the umask is off.  

I've tried both of these lines in my fstab:
```
//192.168.0.100/videos          /home/scv5/tv    cifs    noauto,users,rw,umask=000       0       0                     
#//192.168.0.100/videos                 /home/scv5/bedroom       cifs    defaults        0       0
```
Both have the same result.   From the 192.168.0.100's /etc/samba/smb.conf:

```
[videos]
comment = Videos
path = /var/lib/mythtv/videos
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = mythtv
force group = mythtv
```
and perms for that directory:

```
drwxrwxrwx 58 regular_user regular_user 12288 2009-08-15 13:20 videos
```
and my /etc/profile has my umask set at 022.

Basically i want it to stop prompting me for a password on mount and for it to not give any permission problems when moving/copying directories and files over.

---

### Post by DigitalDuality on 2009-08-29
bump

---

