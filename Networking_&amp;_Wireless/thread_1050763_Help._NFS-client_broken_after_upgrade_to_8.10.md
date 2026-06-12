---
title: "Help. NFS-client broken after upgrade to 8.10"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Azyx on 2009-01-26
Hi. I have a dual networks one 1Gbit and one 100Mbit. Both my NFS-client and NFS-server was 8.04 LST. NFS worked very go, no problem at all :) But after upgrade on the NFS-client to 8.10, NFS-shares can not mount. If I run mount -a my message is "internal error"

My **NFS-client** machines fstab.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b801b8d5-8bc5-4b0c-a31c-df7ef0022277 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=a218cdeb-5077-4917-bc0e-b4cea3432d8b /home           ext3    relatime        0       2
# /dev/sda3
UUID=64782f73-67ff-4802-81d7-66586fc6fc9c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#NFS-montering av DasBlack delade diskar. mounteringspunkt i hemma mappen
10.1.1.2:/media/280GB_C /home/a/DasBlack_NFS/280GB_C    nfs rsize=32768,wsize=32768,hard,intr,retry=2 0 0
10.1.1.2:/media/280GB_D /home/a/DasBlack_NFS/280GB_D    nfs rsize=32768,wsize=32768,hard,intr,retry=2 0 0
10.1.1.2:/media/280GB_E /home/a/DasBlack_NFS/280GB_E    nfs rsize=32768,wsize=32768,hard,intr,retry=2 0 0
10.1.1.2:/media/100GB_F /home/a/DasBlack_NFS/100GB_F    nfs rsize=32768,wsize=32768,hard,intr,retry=2 0 0

---------------------------------------

I remember some error.message that say something like... Warning! "New final line is missing" or something about fstab.

**My NFS-servers** exports on a Hardy 8.04 LST machine.

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/media/100GB_F  10.1.1.0/255.255.255.0(rw)
/media/280GB_C  10.1.1.0/255.255.255.0(rw)
/media/280GB_D  10.1.1.0/255.255.255.0(rw)
/media/280GB_E  10.1.1.0/255.255.255.0(rw)
/media/280GB_D  192.168.0.0/255.255.255.0(rw)


Any ideas what's wrong?

Both VNC, SSH and works between the 8.10 and 8.04LTS, it only the NFS-client that broken.

 Other problem is how network settings works? I can't see my configuration in that new thing called 'Network configuration', but ifconfig seems to show the right things. 

The applet "NetworkManager Applet 0.7.0" don't work. 

Thanx /Azyx

---

### Post by ille on 2009-01-30
I did also get the nfs internal error when upgrading to 8.10. Havent got it working yet. Other clients work, just my 8.10 laptop that does not work.

See:

[http://ubuntuforums.org/showthread.php?t=1031919&highlight=nfs+internal+error](http://ubuntuforums.org/showthread.php?t=1031919&highlight=nfs+internal+error)

---

### Post by dmizer on 2009-01-30
> **Azyx said:**
> I remember some error.message that say something like... Warning! "New final line is missing" or something about fstab.

This may be because you edited your fstab in a gui editor like mousepad or gedit. It's a good idea to always use flat text editors like vi or nano to edit critical configure files like fstab.

Try opening your fstab in nano:
```
sudo nano /etc/fstab
```
Make sure there is a blank line at the end of the file (go to the end of the last line and hit <enter>).

Then save the file by hitting <ctrl>+x, type Y (you do want to save the modified buffer), and then hit enter to save the file.

This may fix your problem.

---

### Post by Azyx on 2009-01-30
> **dmizer said:**
> This may be because you edited your fstab in a gui editor like mousepad or gedit. It's a good idea to always use flat text editors like vi or nano to edit critical configure files like fstab.

Try opening your fstab in nano:
```
sudo nano /etc/fstab
```
Make sure there is a blank line at the end of the file (go to the end of the last line and hit <enter>).

Then save the file by hitting <ctrl>+x, type Y (you do want to save the modified buffer), and then hit enter to save the file.

This may fix your problem.

I always use nano, and there are nothing at the last line...
But I don't get the message any more. It's maybee something that happend during upgrade?

But now I'm able to mount with 'sudo mount -a', but it do not automatic mount on boot. :(

I have read something about that ju should mount with automounter or something for a year ago...but it's sad, cos when a finaly upgraded my server from Dapper to Hardy, the mounting worked very, very good. Never failed!! It like Ubuntu are not really compatible between it's releases :(

/Cheers

---

### Post by Azyx on 2009-01-30
> **ille said:**
> I did also get the nfs internal error when upgrading to 8.10. Havent got it working yet. Other clients work, just my 8.10 laptop that does not work.

See:

[http://ubuntuforums.org/showthread.php?t=1031919&highlight=nfs+internal+error](http://ubuntuforums.org/showthread.php?t=1031919&highlight=nfs+internal+error)

I get in and checked Firestarter and tried to see if there was someting strange..didn't really remember so I make a new configuration. And now it's work with mounting with "sudo mount -a" :) but it do not mount automatically on boot :(

---

### Post by dmizer on 2009-01-30
Try this fix: [http://ubuntuforums.org/showthread.php?t=951722](http://ubuntuforums.org/showthread.php?t=951722)

---

### Post by Azyx on 2009-01-31
Didn't work :(
My rc.local look like this:

GNU nano 2.0.7             File: /etc/rc.local                                

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount /home/a/DasBlack_NFS/280GB_C
mount /home/a/DasBlack_NFS/280GB_D
mount /home/a/DasBlack_NFS/280GB_E
mount /home/a/DasBlack_NFS/100GB_F
exit 0

............................................

And /etc/fstab like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b801b8d5-8bc5-4b0c-a31c-df7ef0022277 /               ext3    relatime,erro$
# /dev/sda2
UUID=a218cdeb-5077-4917-bc0e-b4cea3432d8b /home           ext3    relatime     $
# /dev/sda3
UUID=64782f73-67ff-4802-81d7-66586fc6fc9c none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#NFS-montering av DasBlack delade diskar. mounteringspunkt i hemma mappen
10.1.1.2:/media/280GB_C /home/a/DasBlack_NFS/280GB_C    nfs noauto, rsize=32768$
10.1.1.2:/media/280GB_D /home/a/DasBlack_NFS/280GB_D    nfs noauto, rsize=32768$
10.1.1.2:/media/280GB_E /home/a/DasBlack_NFS/280GB_E    nfs noauto, rsize=32768$
10.1.1.2:/media/100GB_F /home/a/DasBlack_NFS/100GB_F    nfs noauto, rsize=32768$

..............................................

/Cheers

---

### Post by Azyx on 2009-01-31
Didn't work :(
My rc.local look like this:

GNU nano 2.0.7             File: /etc/rc.local                                

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount /home/a/DasBlack_NFS/280GB_C
mount /home/a/DasBlack_NFS/280GB_D
mount /home/a/DasBlack_NFS/280GB_E
mount /home/a/DasBlack_NFS/100GB_F
exit 0

............................................

And /etc/fstab like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b801b8d5-8bc5-4b0c-a31c-df7ef0022277 /               ext3    relatime,erro$
# /dev/sda2
UUID=a218cdeb-5077-4917-bc0e-b4cea3432d8b /home           ext3    relatime     $
# /dev/sda3
UUID=64782f73-67ff-4802-81d7-66586fc6fc9c none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#NFS-montering av DasBlack delade diskar. mounteringspunkt i hemma mappen
10.1.1.2:/media/280GB_C /home/a/DasBlack_NFS/280GB_C    nfs noauto, rsize=32768$
10.1.1.2:/media/280GB_D /home/a/DasBlack_NFS/280GB_D    nfs noauto, rsize=32768$
10.1.1.2:/media/280GB_E /home/a/DasBlack_NFS/280GB_E    nfs noauto, rsize=32768$
10.1.1.2:/media/100GB_F /home/a/DasBlack_NFS/100GB_F    nfs noauto, rsize=32768$

..............................................

When i run mount -a I get this message:

a@Intel:~$ sudo mount -a
[sudo] password for a: 
[mntent]: line 13 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
a@Intel:~$ 

..............................................

What did noauto mean in fstab?

Cheers

---

### Post by Azyx on 2009-01-31
> **Azyx said:**
> Didn't work :(
My rc.local look like this:

GNU nano 2.0.7             File: /etc/rc.local                                

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount /home/a/DasBlack_NFS/280GB_C
mount /home/a/DasBlack_NFS/280GB_D
mount /home/a/DasBlack_NFS/280GB_E
mount /home/a/DasBlack_NFS/100GB_F
exit 0

............................................

And /etc/fstab like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b801b8d5-8bc5-4b0c-a31c-df7ef0022277 /               ext3    relatime,erro$
# /dev/sda2
UUID=a218cdeb-5077-4917-bc0e-b4cea3432d8b /home           ext3    relatime     $
# /dev/sda3
UUID=64782f73-67ff-4802-81d7-66586fc6fc9c none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#NFS-montering av DasBlack delade diskar. mounteringspunkt i hemma mappen
10.1.1.2:/media/280GB_C /home/a/DasBlack_NFS/280GB_C    nfs noauto, rsize=32768$
10.1.1.2:/media/280GB_D /home/a/DasBlack_NFS/280GB_D    nfs noauto, rsize=32768$
10.1.1.2:/media/280GB_E /home/a/DasBlack_NFS/280GB_E    nfs noauto, rsize=32768$
10.1.1.2:/media/100GB_F /home/a/DasBlack_NFS/100GB_F    nfs noauto, rsize=32768$

..............................................

When i run mount -a I get this message:

a@Intel:~$ sudo mount -a
[sudo] password for a: 
[mntent]: line 13 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
a@Intel:~$ 

..............................................

What did noauto mean in fstab?

Cheers

I removed 'noauto' from fstab and I worked, at least one time :)

---

### Post by Azyx on 2009-01-31
No, I did NOT work at all, it was only the Disk thats appear  on my desktop :(

---

### Post by dmizer on 2009-01-31
Please post the output of:
```
cat /etc/fstab
```

When you post the contents, be sure to include **code** tags like so:
[noparse]```
fstab output
```[/noparse]

---

### Post by Azyx on 2009-01-31
> **dmizer said:**
> Please post the output of:
```
cat /etc/fstab
```

When you post the contents, be sure to include **code** tags like so:
[noparse]```
fstab output
```[/noparse]

Yes. sorry, I saw now that my line have being cut.

Commands in **bold**
...................

```
**a@Intel:~$ sudo mount -a**
[mntent]: line 13 in /etc/fstab is bad
[mntent]: line 14 in /etc/fstab is bad
[mntent]: line 15 in /etc/fstab is bad
[mntent]: line 16 in /etc/fstab is bad
**a@Intel:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b801b8d5-8bc5-4b0c-a31c-df7ef0022277 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=a218cdeb-5077-4917-bc0e-b4cea3432d8b /home           ext3    relatime        0       2
# /dev/sda3
UUID=64782f73-67ff-4802-81d7-66586fc6fc9c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#NFS-montering av DasBlack delade diskar. mounteringspunkt i hemma mappen
10.1.1.2:/media/280GB_C /home/a/DasBlack_NFS/280GB_C    nfs noauto, rsize=32768,wsize=32768,hard,intr,retry=2 0 0
10.1.1.2:/media/280GB_D /home/a/DasBlack_NFS/280GB_D    nfs noauto, rsize=32768,wsize=32768,hard,intr,retry=2 0 0
10.1.1.2:/media/280GB_E /home/a/DasBlack_NFS/280GB_E    nfs noauto, rsize=32768,wsize=32768,hard,intr,retry=2 0 0
10.1.1.2:/media/100GB_F /home/a/DasBlack_NFS/100GB_F    nfs noauto, rsize=32768,wsize=32768,hard,intr,retry=2 0 0
**a@Intel:~$ cat /etc/rc.local**
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount /home/a/DasBlack_NFS/280GB_C
mount /home/a/DasBlack_NFS/280GB_D
mount /home/a/DasBlack_NFS/280GB_E
mount /home/a/DasBlack_NFS/100GB_F
exit 0
a@Intel:~$
```

---

### Post by Azyx on 2009-01-31
Thanx dmizer :)

I find the error. It seems to be the space I have after **noauto** was the problem. Thank you very much :)

/Cheers

---

### Post by dmizer on 2009-01-31
> **Azyx said:**
> Thanx dmizer :)

I find the error. It seems to be the space I have after **noauto** was the problem. Thank you very much :)

/Cheers

Good deal! :)

---

