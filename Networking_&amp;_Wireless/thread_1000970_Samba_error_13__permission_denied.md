---
title: "Samba: error 13 : permission denied"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by on5sl on 2008-12-03
Hello,

I've got a freebsd server which runs samba. This samba share has file permissions and samba permissions "activated". Everything works well on the system administrator account, but not on the other user accounts...
When i do mount /home/bram/nas with the user bram everything is fine:

```
bram@katia-desktop:~$ mount /home/bram/nas/
bram@katia-desktop:~$ df -h
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda3              92G   18G   70G  21% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  332K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2,7M  249M   2% /dev
tmpfs                 252M  224K  251M   1% /dev/shm
lrm                   252M  2,0M  250M   1% /lib/modules/2.6.27-9-generic/volatile
//192.168.0.10/main   1,4T  648G  719G  48% /home/bram/nas
bram@katia-desktop:~$ 

```

Here is a comparization of the two users:

```
bram@katia-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#[cut out not relevant]

# NAS Server
//192.168.0.10/main /home/bram/nas cifs credentials=/home/bram/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=bram,gid=bram,noauto,user 0 0
//192.168.0.10/main /home/katia/nas cifs credentials=/home/katia/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=katia,gid=katia,noauto,user 0 0
//192.168.0.10/main /home/hanne/nas cifs credentials=/home/hanne/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=hanne,gid=hanne,noauto,user 0 0
//192.168.0.10/main /home/laura/nas cifs credentials=/home/laura/.smbpasswd,iocharset=utf8,file_mode=0777,dir_mode=0777,uid=laura,gid=laura,noauto,user 0 0
bram@katia-desktop:~$ sudo cat /home/bram/.smbpasswd /home/katia/.smbpasswd 

[sudo] password for bram: 
username=bram
password=xxxxxxxxxxxx
username=katia
password=xxxxxxxxxxxxx

bram@katia-desktop:~$ sudo ls -ld /home/bram/nas /home/katia/nas
drwxr-xr-x 2 bram  bram  4096 2008-12-01 23:54 /home/bram/nas
drwxr-xr-x 2 katia katia 4096 2008-12-01 23:57 /home/katia/nas

bram@katia-desktop:~$ sudo ls -ld /home/bram/.smbpasswd /home/katia/.smbpasswd 
-rw-r--r-- 1 bram  bram  36 2008-12-01 22:38 /home/bram/.smbpasswd
-rw-r--r-- 1 katia katia 38 2008-12-01 23:42 /home/katia/.smbpasswd
```

As you can see, everything is the same? I've also tried to activate some more user right in users/groups but that doesn't help...
I did search after another solution and found that the nounix option could help..but still the same error :(
I really don't get the issue...maybe it is a bug? I

edit:
and yes, I've read [this]("http://ubuntuforums.org/showthread.php?t=288534") thread off course...maybe it's more relevant to post my question there?
I can also read in the cifs page that when using the option user it tries to apply the user on currently logged in...the user option in my fstab is for my ubuntu so that every user can mount it...and the credentials are used to specify the samba user. Maybe there is going something wrong there?

---

### Post by uvdevnull on 2009-01-15
> **on5sl said:**
> ...and the credentials are used to specify the samba user. Maybe there is going something wrong there?

Did you ever fix this? If not, let's see the contents of your credentials file...

---

