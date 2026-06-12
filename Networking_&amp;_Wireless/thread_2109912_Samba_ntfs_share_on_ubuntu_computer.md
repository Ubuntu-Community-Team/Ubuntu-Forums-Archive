---
title: "Samba ntfs share on ubuntu computer"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by dummyhead3 on 2013-01-28
I am trying to share a folder which is on an ntfs partition. The share appears in the list but remains inaccessible. 
I am running ubuntu 12.04 32bit on an Intel i3.
Any tips?
Thanks

---

### Post by Morbius1 on 2013-01-29
Is the NTFS partition mounted?
If it is mounted how is it mounted?

If you are mounting it manually through Nautilus for example it will be accessible only to you. You may have set up a guest share in Samba but it can't override Linux permissions so you have 2 choices:

[1] Have the NTFS partition mount at boot with the correct permissions.

I do not recommend using PySDM, mountmanager, Disks, or any of the other utilities to do this especially if you have multiple partitions on multiple drives and especially if you dual boot with Windows. I like templates better. If you post the output of the following commands I can assist you with this:
```
sudo blkid -c /dev/null
cat /etc/fstab
```[2] The easier way ( especially if this is on an external USB type device ) is to force the remote user to appear to be you for this share.

You would edit /etc/samba/smb.conf and add the following line:
```
force user = morbius
```[COLOR=Blue]*Changing morbius to your own Linux login user name.*[/COLOR]

Where you put that line depends on how you created the Samba share - there are 2 methods - one in smb.conf and one through Nautilus. If you created it in Nautilus then add it to the [global] section. If the share definition is in smb.conf itself then add it to the share definition. If you have no idea what I'm talking about post the output of these commands and I can tell you where to place it:
```
testparm -s
net userhsare info --long

```

---

### Post by dummyhead3 on 2013-01-29
Thanks a lot I solved it! Instead of using udisks to do a pre-user mount I set up the Windows partition to mount the partition system-wide in /etc/fstab.
If you have this problem, check out:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) for more details about auto-mounting partitions.
For editing fstab: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

