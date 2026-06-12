---
title: "Trouble mounting smb drives from my file server"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by MrSam on 2006-06-11
I have 2 Centos server boxes running - one for file server and the other is my practice web server. The file server is set up with Samba and has been working great - access with no problem from both the second Linux box and from XP.

I have install a dual boot to Ubuntu/XP on my main machine and am looking at moving everything to Ubuntu but I'm struggling a little.

The problem I am having now is getting Ubuntu to auto mount the drives at bootup. I have a credentials file (/ect/samba/sambapass) that contains this:
> Username:
username=name

Password:
password=pass

I have edited my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.0.25/LDrive2 /home/gene/smbmnt1 smbfs credentials=/etc/samba/sambapass,rw,uid=gene 0 0
//192.168.0.25/Sata1 /home/gene/smbmnt2 smbfs credentials=/etc/samba/sambapass,rw, uid=gene 0 0
//192.168.0.25/Sata2 /home/gene/smbmnt3 smbfs credentials=/etc/samba/sambapass,rw, uid=gene 0 0


But when I reboot and look in the mount folders they are empty. I have a similar setup on my second Centos box and it is working with no problems.

---

### Post by MrSam on 2006-06-11
I found an post that said that default for all mounts is in /media so I changed the mount points to /media/smbmnt1 and so forth to 3 but still can't mount the drives. Here is the terminal output:
```
gene@gene-ubuntu:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //192.168.0.25/LDrive2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //192.168.0.25/Sata1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on //192.168.0.25/Sata2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by MrSam on 2006-06-11
Anybody out there that understands this stuff?

HELP!! :lol: 

And thanks for anything you can point me to.

---

### Post by ZenithUK on 2006-06-14
You need to install smbfs support before you can get your samba shares to automount.

Go to System > Administration > Synaptic Package Manager
Enter password.
Find **smbfs** and then highlight it for installation (right mouse click).
Once it is installed, open a console and type the following:```
sudo mount -a
```And voila!  Your problems should just disappear (hopefully).
Put it this way, I'm quite new to all this as well, and this is how I fixed it a few minutes ago.  :)

---

