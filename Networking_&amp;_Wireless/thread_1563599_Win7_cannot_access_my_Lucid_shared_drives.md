---
title: "Win7 cannot access my Lucid shared drives"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by pappo on 2010-08-29
My linux pc has 3 hard drives.
one with linux OS, a second internal 500Gb drive, and one 300Gb external USB.
I am sharing my home directories and both drives using SWAT.
The drives are at /media/Backup300 and /media/Backup500.

My Win7 laptop can see my home directory and r/w files to it.
My Win7 laptop sees the shares for the 300 and 500Gb drives, but when I try to open them I get the Windows error code 0x80070035 "The network path was not found"

Any ideas ???
I am attaching my smb.conf file

---

### Post by Morbius1 on 2010-08-29
What are the Linux permissions on the two partitions:

```
ls -dl /media/Backup300
```
```
ls -dl /media/Backup500
```

---

### Post by pappo on 2010-08-29
> **Morbius1 said:**
> What are the Linux permissions on the two partitions:

```
ls -dl /media/Backup300
```
```
ls -dl /media/Backup500
```


drwx------   1 xxxxx xxxxx 36864 2010-07-22 18:58 Backup300/
drwx------ 127 xxxxx xxxxx  4096 2010-07-22 18:58 Backup500/

---

### Post by Morbius1 on 2010-08-29
> drwx------   1 xxxxx xxxxx 36864 2010-07-22 18:58 Backup300/
drwx------ 127 xxxxx xxxxx  4096 2010-07-22 18:58 Backup500/     That's why you can't access it remotely. Samba says that the remote user can access the share but Linux file permissions says the only user that has access is "xxxxx".

2 ways to solve this:

Change linux permissions on Backup300 and and Backup500 so that a remote user can access it. Maybe 777 or 770 depending on how you set up your samba users.

Or, add the following line to the share definition for each share:
```
force user = xxxxx
```xxxxx is the only user that has access. force user will act as a mask and convert the remote user to xxxxx, at least as far as that share is concerned.

---

### Post by pappo on 2010-08-29
> **Morbius1 said:**
> That's why you can't access it remotely. Samba says that the remote user can access the share but Linux file permissions says the only user that has access is "xxxxx".

2 ways to solve this:

Change linux permissions on Backup300 and and Backup500 so that a remote user can access it. Maybe 777 or 770 depending on how you set up your samba users.

Or, add the following line to the share definition for each share:
```
force user = xxxxx
```xxxxx is the only user that has access. force user will act as a mask and convert the remote user to xxxxx, at least as far as that share is concerned.

Morbius1 - When I got to the /media directory and enter "sudo chmod 777 /media/Backup300 or chmod 777 /media/Backup500, the permissions do not change ?? Why is that ?

I also tried adding force user = myusername to my smb.conf, but Win7 is still being denied access.

---

### Post by Morbius1 on 2010-08-29
Sound like they are formatted in NTFS or FAT32. Can't chown or chmod a Windows filesystem.

I would go with the "force user" option.

---

### Post by pappo on 2010-08-29
> **Morbius1 said:**
> Sound like they are formatted in NTFS or FAT32. Can't chown or chmod a Windows filesystem.


The 500G drive is Linux EXT4:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

the 300G is not:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36483   293049666    7  HPFS/NTFS

---

### Post by pappo on 2010-08-29
> **Morbius1 said:**
> Sound like they are formatted in NTFS or FAT32. Can't chown or chmod a Windows filesystem.

I would go with the "force user" option.

Is this the right way to add it:


[/media/Backup500]
        comment = Backup500
        path = /media/Backup500
        valid users = %S
        admin users = myusername
        force user = myusername
        read only = No
        create mask = 0775
        directory mask = 0775
        hosts allow = 192.168.0.

---

### Post by Morbius1 on 2010-08-29
Serves my right for not looking that carefully at your share definitions. I didn't realize you were using "admin users". Doesn't make any sense to use force user and admin user in the same share when they point to the same username.

The NTFS formatted drive is going to get tricky if the share is set up the same way.

The ext4 is a mystery to me. This should have worked:
```
sudo chmod 777 /media/Backup500 
```
At least it should have made it so the remote user could add to the directory. 

Let me ponder this.

---

### Post by Morbius1 on 2010-08-29
Is the ext4 partition being mounted automatically in fstab?
Can you post the output of the following command:
```
cat /etc/fstab
```

---

### Post by pappo on 2010-08-29
> **Morbius1 said:**
> Is the ext4 partition being mounted automatically in fstab?
Can you post the output of the following command:
```
cat /etc/fstab
```

Should I get rid of the admin user and just keep the force user ?

I did not put the 300Gb drive in fstab because it is an external USB drive that is always connected and always comes up automatically.

Here is my fstab output:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ef62a2b0-2395-4ca4-88ea-e495dbfb1120 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ded5bd7c-a537-4648-98e4-156d2e5c0bd1 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=546d32fb-fa00-42e5-b985-88e928768f82 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#Backup500
UUID=eb40c742-2c7d-4b08-a608-a3daf4b1a863 /media/Backup500	ext4	defaults0	2

---

### Post by Morbius1 on 2010-08-29
>  UUID=eb40c742-2c7d-4b08-a608-a3daf4b1a863 /media/Backup500    ext4    [COLOR=Blue]defaults0    2[/COLOR]I don't know if that's a typo but there should be a space between "defaults" and "0 2" --- > [COLOR=Blue]defaults 0 2[/COLOR]

If that's not a typo I would add the space, unmount /media/Backup500 if it's really mounted there and issue the following command to remount /media/Backup500:
```
sudo mount -a
```I'm obsessed with the following command not working:
```
 sudo chmod 777 /media/Backup500
```It has to work. And when it does you won't need the "force user" for that share.

---

### Post by pappo on 2010-08-29
> **Morbius1 said:**
> I don't know if that's a typo but there should be a space between "defaults" and "0 2" --- > [COLOR=Blue]defaults 0 2[/COLOR]

If that's not a typo I would add the space, unmount /media/Backup500 if it's really mounted there and issue the following command to remount /media/Backup500:
```
sudo mount -a
```I'm obsessed with the following command not working:
```
 sudo chmod 777 /media/Backup500
```It has to work. And when it does you won't need the "force user" for that share.

It is a typo because there is a space between defaults and 0 2.
Also, I went back and did the "sudo chmod 777 /media/Backup500 and it worked.  Now it looks like this:
drwxrwxrwx 127     777 xxxxx  4096 2010-07-22 18:58 Backup500/

I restarted samba but nothing has changed.  I can still open and r/w to my ubuntu pc home directory from my Win7 laptop, but not the two hard drives.

---

### Post by Morbius1 on 2010-08-30
Open smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Find these two share definitions:
> [[COLOR=Blue]/media/Backup500[/COLOR]]
        comment = Backup500
        path = /media/Backup500
        valid users = %S
        admin users = myusername
        force user = myusername
        read only = No
        create mask = 0775
        directory mask = 0775
        hosts allow = 192.168.0.     

[[COLOR=Blue]/media/Backup300[/COLOR]]
    comment = Backup300
    path = /media/Backup300
    username = psteege
    valid users = %S
    admin users = psteege
    read only = No
create mask = 0775
    directory mask = 0775
    hosts allow = 192.168.0.And change the share names like this:
> [[COLOR=Blue]Backup500[/COLOR]]
        comment = Backup500
        path = /media/Backup500
        valid users = %S
        admin users = myusername
        force user = myusername
        read only = No
        create mask = 0775
        directory mask = 0775
        hosts allow = 192.168.0.     

[[COLOR=Blue]Backup300[/COLOR]]
    comment = Backup300
    path = /media/Backup300
    username = psteege
    valid users = %S
    admin users = psteege
    read only = No
create mask = 0775
    directory mask = 0775
    hosts allow = 192.168.0.Save smb.conf, exit gedit and back in the terminal restart samba:
```
sudo service smbd restart
```

---

### Post by pappo on 2010-08-30
> **Morbius1 said:**
> 

I went to a very basic smb.conf file and it all is working now.
I can read/write my home directory and both hard drives (Backup300 & Backup500)

Here is my smb.conf

[global]
   workgroup = MSHOME
   server string = Ubuntu10
   hosts allow =  192.168.0.
;   printcap name = /etc/printcap
   load printers = yes
   printing = lprng
;   guest account = smbuser
   log file = /var/log/samba/%m.log
   ;max log size = 0
   security = user
   encrypt passwords = true
   smb passwd file = /etc/samba/smbpasswd
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   dns proxy = no 
   log level = 2
   debug level = 2

[Ubuntu_Home]
   path = /home/username
   writable = yes
   valid users = username,smbuser
   browseable = yes
   public = yes

[Backup300]
   path = /media/Backup300
   writable = yes
   valid users = username,smbuser
   browseable = yes
   public = yes

[Backup500]
   path = /media/Backup500
   writable = yes
   valid users = username,smbuser
   browseable = yes
   public = yes

Thanks for all your assistance Morbius1.  I learned a lot in the process of researching your tips and suggestions.  I will cast this smb.conf in granite and save for the future.

Best regards

---

