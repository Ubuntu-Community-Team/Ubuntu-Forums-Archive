---
title: "Mount network folders on boot-up, and allow all users to read/write"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by Tristan9669 on 2006-07-01
I'm trying to mount network folders on boot-up, and allow all users to read/write but nothing happens, when I go to the directory where I mounted it, nothing is there. By the way, I'm trying to mount folders from a XP PRO SP2 machine that doesn't have a password. When I mount the network folders manually using ```
sudo mount //192.168.1.102/Videos /media/Justin/Videos -o dmask=777,fmask=777
``` it works fine. Can anyone help?

Here is my fstab.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/hda5     ntfs    nls=utf8,umask=0222 0       0
/dev/hda8       /media/hda8     vfat    iocharset=utf8,umask=000 0       0
/dev/hdb1       /media/hdb1     ntfs    nls=utf8,umask=0222 0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.1.102/Downloads    /media/Justin/Downloads smbfs  dmask=777,fmask=777  0    0
//192.168.1.102/SharedDocs    /media/Justin/SharedDocs smbfs  dmask=777,fmask=777  0    0
//192.168.1.102/Videos    /media/Justin/Videos smbfs  dmask=777,fmask=777  0    0

```

---

### Post by tturrisi on 2006-07-01
XP Pro?
You cannot access shares on XP Pro without a password unless xp is using Simple File Sharing and if so the only availabe shares will be the default shares of username/shared documents.  Best to not use simple file sharing on xp and then use computer mgmt to add a user (the ubuntu username) and then share a dir & set permissions for it.  Then config ubuntu as so:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Tristan9669 on 2006-07-01
[QUOTE=tturrisi]XP Pro?
You cannot access shares on XP Pro without a password unless xp is using Simple File Sharing and if so the only availabe shares will be the default shares of username/shared documents.  Best to not use simple file sharing on xp and then use computer mgmt to add a user (the ubuntu username) and then share a dir & set permissions for it.  Then config ubuntu as so:

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)[/QUOTE]
is there anyway to do it with simple file sharing. I don't understand why it works when I manually mount it but not on boot-up

---

### Post by tturrisi on 2006-07-02
[QUOTE=Tristan9669]is there anyway to do it with simple file sharing. I don't understand why it works when I manually mount it but not on boot-up[/QUOTE]
Try setting the permissions on the windows shares, i.e. when in xp rt click the shared windows dir > sharing tab > permissions
If get a prompt like "permissions cannot be set or shared for admin purposes only then create a new share and set permissions for it using your ubuntu userame & password.

If use xppro then you should never be using simple file sharing anyway.

---

### Post by Tristan9669 on 2006-07-03
[QUOTE=tturrisi]Try setting the permissions on the windows shares, i.e. when in xp rt click the shared windows dir > sharing tab > permissions
If get a prompt like "permissions cannot be set or shared for admin purposes only then create a new share and set permissions for it using your ubuntu userame & password.

If use xppro then you should never be using simple file sharing anyway.[/QUOTE]
I finally got it to work using this.
```
//192.168.1.102/Videos    /media/Justin/Videos cifs  uid=1000,umask=777  0    0
```

---

### Post by Pirate_Pete on 2006-09-04
tturrisi is right, by default xp pro does not allow a blank password. However, changing it to simple file sharing will not solve this problem.

XP Pro can be changed to allow for login with a blank password, Its the only way for a user account that does not have a password.

To enable this go in windows go to Start -> Run -> "gpedit.msc"
Windows Settings -> Security Settings -> Local Policies -> Security Options
Double click on "Accounts: Limit local account use of blank passwords to console logon only" and check disabled

This will now allow a user to use the share without entering a password.

XP Home allows blank password login by default

---

### Post by Tristan9669 on 2006-09-04
yes it does, I have xp pro sp2 with simple sharing and using

```

//192.168.1.102/Videos    /media/Justin/Videos cifs  uid=1000,umask=777  0    0
``` lets me mount network folders on boot-up, and allow all users to read/write perfectly fine, maybe its because my xp account isn't password protected.

---

### Post by tturrisi on 2006-09-05
Chances are that the use Justin on xppro is not a member of the xp admin group, but a secondary user.

---

### Post by Tristan9669 on 2006-09-05
no, there is only one xp account and its admin by default

---

