---
title: "NFS refused mount request ... (/): no export entry | OS X client"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by gellpak on 2012-09-09
Having trouble getting samba going so I searched around and discovered NFS.

I followed this guide:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

for the ubuntu side (12.04). 

Here's the mount point in my /etc/exports file:

```
/media/cerberus *(rw,no_subtree_check,sync,insecure,all_squash)
```

I didn't do anything in fstab as the disk in question is already a raid array that's mounted in the same location (/media/cerberus).

When I try to access the share from OS X 10.8, I get a permission denied error, and on the ubuntu side I get this in /var/log/syslog:

```
Sep  9 16:59:16 mediacenter rpc.mountd[15198]: refused mount request from 192.168.1.104 for /cerberus (/): no export entry
```

I just want to set up a network share and both samba and nfs are giving me nothing. Any ideas?

---

### Post by LewisTM on 2012-09-10
Can you mount but not access the share?
My first idea would be that your /media/cerberus directory does not have rx permissions for 'others' users. Since you export with all_squash, all users become user nobody of group nogroup so to even access the share you need to enable others to view the files and folders.

See if that helps
```
sudo chmod o+rx /media/cerberus
```

Also you could try to mount the share locally:
```
sudo chmod 777 /mnt
sudo mount localhost:/media/cerberus /mnt
cd /mnt
```
If you get the same kind of error then it's a permission problem. If not, it's probably a Mac-specific problem and you would be more lucky by posting in a Mac forum.

Cheers!

---

### Post by spjackson on 2012-09-10
You are exporting /media/cerberus but from the syslog message it looks like you are trying to mount ubuntu-server:/cerberus

Instead you need to mount ubuntu-server:/media/cerberus

If this isn't it, then we need to know more about what you are doing on the OSX side.

---

### Post by gellpak on 2012-09-10
It worked! I (for some reason) thought I had some sort of alias situation where /cerberus would point directly to /media/cerberus. Obviously not.

---

