---
title: "Shared External USB Hard Drive: Browesable, but no write privileges"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by grossinm on 2009-01-05
Setup Xubuntu 8.10 on an old Dell Dimension 4700c

Setup Samba and am sharing the home directories just fine (read write, no problem from my IMac 10.5.6), but that drive home drive is only 40gb. 

So, I add a 1TB WD My Book.  My smb.conf reads:

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "miller"
netbios name = "millerserver"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700

[storage]
        comment = ITunes
        path = /media/Storage/
        browseable = yes
        read only = no
        guest ok = no
        create mask = 0644

I restart Samba, but cannot write to the folder.

I change the permissions CHMOD 0777 /media/Storage and restart Samba, still, no priviledges.

This seems to be a common problem, but I cannot find the solution.

---

### Post by grossinm on 2009-01-05
More info:

grossinm@millerserver:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         146     1172713+  83  Linux
/dev/sda2             147        4863    37889302+   5  Extended
/dev/sda5            4677        4863     1502046   82  Linux swap / Solaris
/dev/sda6             147        4489    34885084+  83  Linux
/dev/sda7            4490        4676     1502046   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

---

### Post by grossinm on 2009-01-05
And more...

grossinm@millerserver:~$ dmesg | tail
[ 7616.948022] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 7891.952022] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 8050.944026] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 8435.944033] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 8502.944022] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 8575.948025] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 8614.944021] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 8853.940533] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 9106.948033] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 9625.944022] usb 5-4: reset high speed USB device using ehci_hcd and address 3
grossinm@millerserver:~$

grossinm@millerserver:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              33G  2.7G   29G   9% /
tmpfs                 251M     0  251M   0% /lib/init/rw
varrun                251M  512K  250M   1% /var/run
varlock               251M     0  251M   0% /var/lock
udev                  251M  2.8M  248M   2% /dev
tmpfs                 251M     0  251M   0% /dev/shm
lrm                   251M  2.0M  249M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             932G   94M  932G   1% /media/Storage

---

### Post by albinootje on 2009-01-05
> **grossinm said:**
> 
[storage]
        comment = ITunes
        path = /media/Storage/
        browseable = yes
        read only = no
        guest ok = no
        create mask = 0644


# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
#    writable = no

Did you try with "writable = yes" ?

And you have "guest ok = no", but at the same time you don't use the "valid users =".
Do you want to use samba users or do you want it available for everyone on the LAN ?

---

### Post by Mandle on 2009-01-05
One workaround I've found, is to mount the drive somewhere in the home folder.  Set it in the fstab, and redirect your samba.conf, restart and should work.  Not nessasarily the most secure method, but it does work.

---

### Post by grossinm on 2009-01-05
First, I tried albinootje fix.  edited smb.conf to read:

[storage]
        comment = ITunes
        path = /media/Storage/
        browseable = yes
        read only = yes
        writable = yes
        guest ok = yes
        create mask = 0644
        directory mask = 0755
        force user = grossinm
        force group = grossinm

I also tried read only = No, and that did not work as well.

Mandle, I'm not sure how to edit fstab.  

Thanks

---

### Post by grossinm on 2009-01-05
One question keeps coming back to me.  Why is the external drive treated differently than the internal drive?  

I had no trouble sharing the internal drive (which I gather is what Mandle want's me to do and make the external drive reside w/in the home directories like an internal drive.).

I really just need to implement a solid solution, since it will be serving music/videos to family (and therefore needs 99.99999% reliability).

---

### Post by albinootje on 2009-01-05
> **grossinm said:**
> First, I tried albinootje fix.  edited smb.conf to read:

[storage]
        comment = ITunes
        path = /media/Storage/
        browseable = yes
        read only = yes
        writable = yes
        guest ok = yes
        create mask = 0644
        directory mask = 0755
        force user = grossinm
        force group = grossinm

I also tried read only = No, and that did not work as well.


Did you restart samba after those changes ?
And please remove or change the "read only = yes" line.

```

sudo /etc/init.d/samba restart

```
I strongly suggest to check the possible access and permission problems fist via smbclient on your Ubuntu box yourself :
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
This section -> Samba Client Manual Configuration

For example :
```

smbclient //localhost/storage

```
Press enter when it asks for a password, to use anonymous access.

---

### Post by grossinm on 2009-01-05
smb.conf now reads:

[storage]
        comment = ITunes
        path = /media/Storage/
        browseable = yes
        writeable = yes
        guest ok = yes
        create mask = 0644
        directory mask = 0755
        force user = grossinm
        force group = grossinm

Restarted the samba server, no changes in write access from remote machines.

Logged in to the local host both as the user and anonymously.

and then I tried to mkdir (both anonymously and as my user):

smb: \> mkdir test
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test
smb: \> 

Now why did it do that?

---

### Post by albinootje on 2009-01-05
> **grossinm said:**
> 
How can I ensure that my local anonymous login can write to the share?  (touch?)

Can you read this and comply with those requirements ?
(From : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba))

So you have to check the line "guest account =", and set permissions for that "guest user".

> 
Finally, the public share

[public]
        comment = Public Share
        path = /path/to/share/point
        read only = no
        guest only = yes
        guest ok = yes

Again, path is the path to the directory that you want to share out. read only = no will allow users to write to this share. guest only = yes and guest ok = yes will allow guest logins and also force users to login as guests. The user you specified with guest account in the [global] section must have write permissions on /path/to/share/point in order to write files to the share.


---

### Post by albinootje on 2009-01-05
I've just tested it with the following :

My /etc/samba/smb.conf on the local fileserver has this :
```

guest account = nobody
[test1]
   comment = test1
   path = /home/samba/test1
   public = yes 
   guest ok = yes   
   writable = yes  
   read only = No
   directory mask = 0775

```
Done this :
chown -R nobody /home/samba/test1

> 
$ smbclient //ftp/test1 
  (my local fileserver is known as "ftp" in my /etc/hosts)
Enter guest's password: 
Anonymous login successful
Domain=[TESTING] OS=[Unix] Server=[Samba 3.0.24]
smb: \> ls
  .                                   D        0  Mon Jan  5 22:50:34 2009
  ..                                  D        0  Tue Dec 23 03:28:19 2008

smb: \> mkdir test
smb: \> ls
  .                                   D        0  Mon Jan  5 22:57:54 2009
  ..                                  D        0  Tue Dec 23 03:28:19 2008
  test                                D        0  Mon Jan  5 22:57:54 2009


---

### Post by grossinm on 2009-01-05
Here is what I did:

grossinm@millerserver:~$ sudo nano smb.conf
grossinm@millerserver:~$ chown -R nobody /media/Storage/
grossinm@millerserver:~$ sudo /etc/init.d/samba restart
[sudo] password for grossinm: 
 * Stopping Samba daemons                                                [ OK ] 
 * Starting Samba daemons                                                [ OK ] 
grossinm@millerserver:~$ smbclient //localhost/Storage/
Enter grossinm's password: 
Anonymous login successful
Domain=[MILLER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> ls
  .                                   D        0  Mon Jan  5 10:56:30 2009
  ..                                  D        0  Mon Jan  5 10:58:32 2009
  System Volume Information           D        0  Mon Jan  5 10:56:30 2009

		59616 blocks of size 16777216. 59610 blocks available
smb: \> mkdir test
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test
smb: \> ls
  .                                   D        0  Mon Jan  5 10:56:30 2009
  ..                                  D        0  Mon Jan  5 10:58:32 2009
  System Volume Information           D        0  Mon Jan  5 10:56:30 2009

		59616 blocks of size 16777216. 59610 blocks available
smb: \> 

Still not able to write to the samba share Storage.  Then I tried it with my Grossinm (homes) directory, using my password, and it worked just fine.

So it works just fine on the homes directory (internal drive), but on Storage, an external drive it does not work.

I think it has to do with the permissions (ownership) by Root....  

Thanks for the help (really!).

---

### Post by albinootje on 2009-01-05
> **grossinm said:**
> 
I think it has to do with the permissions (ownership) by Root....  


I've glanced through this whole thread, maybe I missed something.

Is your drive FAT32 or NTFS formatted ?
Can you please post the output of the following, when the drive is attached and mounted :
```

mount

```

---

### Post by grossinm on 2009-01-05
It is NTFS formatted. Mount output:

grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
grossinm@millerserver:~$

---

### Post by albinootje on 2009-01-05
> **grossinm said:**
>  /dev/sdb1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

Thanks.
Can you do the following, where the second line is one long line :
```

sudo umount /dev/sdb1
sudo mount /dev/sdb1 /media/Storage -t ntfs-3g -o umask=000,uid=1000,gid=1000

```
After that try smbclient with your username and try writing to the share.

---

### Post by grossinm on 2009-01-05
It umount just fine, but when I ran the long command I got this:

grossinm@millerserver:~$  sudo mount /dev/sdb1 /media/Storage -t ntfs-3g -o umask=000,uid=1000,gid=1000
fuse: failed to access mountpoint /media/Storage: No such file or directory
grossinm@millerserver:~$

---

### Post by albinootje on 2009-01-05
> **grossinm said:**
> 
fuse: failed to access mountpoint /media/Storage: No such file or directory
grossinm@millerserver:~$

OK. Can you try this instead :
```

sudo umount /dev/sdb1
sudo mkdir /media/Storage
sudo mount /dev/sdb1 /media/Storage -t ntfs-3g -o umask=000,uid=1000,gid=1000

```

---

### Post by grossinm on 2009-01-05
Ok, I followed the command, it seemed to work, but when I logged in as myself (smbclient), it was still write protected.  I tried restarting the samba server and trying again, but no luck.  Here is the terminal output (along w/ some noob errors):

grossinm@millerserver:~$ sudo umount /dev/sdb1
grossinm@millerserver:~$ sudo mkdir /media/Storage
grossinm@millerserver:~$ sudo mount /dev/sdb1 /media/Storage -t ntfs-3g -o umask=000,uid=1000,gid=1000
grossinm@millerserver:~$ smbClient //localhost/Storage
bash: smbClient: command not found
grossinm@millerserver:~$ smbClient //localhost/Storage/
bash: smbClient: command not found
grossinm@millerserver:~$ smbclient //localhost/Storage/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> ls
  .                                   D        0  Mon Jan  5 10:56:30 2009
  ..                                  D        0  Mon Jan  5 16:05:28 2009
  System Volume Information           D        0  Mon Jan  5 10:56:30 2009

		59616 blocks of size 16777216. 59610 blocks available
smb: \> mkdir test
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test
smb: \> sudo /etc/init.d/samba restart
sudo: command not found
smb: \> quite
quite: command not found
smb: \> quit
grossinm@millerserver:~$ sudo /etc/init.d/samaba restart
sudo: /etc/init.d/samaba: command not found
grossinm@millerserver:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                                               [ OK ] 
 * Starting Samba daemons                                                                               [ OK ] 
grossinm@millerserver:~$ smbclient //localhost/Storage/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> ls
  .                                   D        0  Mon Jan  5 10:56:30 2009
  ..                                  D        0  Mon Jan  5 16:05:28 2009
  System Volume Information           D        0  Mon Jan  5 10:56:30 2009

		59616 blocks of size 16777216. 59610 blocks available
smb: \> mkdir test
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test
smb: \>

---

### Post by grossinm on 2009-01-05
One thing did change.  The permissions for the Storage folder are  no longer w/ root, they are now with Grossinm (Read & Write).

---

### Post by albinootje on 2009-01-05
> **grossinm said:**
> 
smb: \> mkdir test
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test
smb: \>

Is your user grossinm the first user made during the Ubuntu installation ?
If so, then uid=1000 and gid=1000 should be correct.

You can check this with the following command :
```

id

```
And can show the output of the mount command again, please ?
```

mount

```

---

### Post by albinootje on 2009-01-05
And can you also this, just in case :
```

ls -la /media
chown -R grossinm /media/Storage

```

---

### Post by grossinm on 2009-01-05
Terminal output:

grossinm@millerserver:~$ id
uid=1000(grossinm) gid=1000(grossinm) groups=4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare),1000(grossinm)
grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
grossinm@millerserver:~$ ls -la /media
total 16
drwxr-xr-x  4 root     root     4096 2009-01-05 16:05 .
drwxr-xr-x 20 root     root     4096 2009-01-04 14:41 ..
lrwxrwxrwx  1 root     root        6 2009-01-04 13:59 cdrom -> cdrom0
drwxr-xr-x  2 root     root     4096 2009-01-04 13:59 cdrom0
-rw-r--r--  1 root     root        0 2009-01-05 16:03 .hal-mtab
-rw-------  1 root     root        0 2009-01-05 10:18 .hal-mtab-lock
drwxrwxrwx  1 grossinm grossinm 4096 2009-01-05 10:56 Storage
grossinm@millerserver:~$ chown -R grossinm /media/Storage
grossinm@millerserver:~$

---

### Post by grossinm on 2009-01-05
Just to keep it all current, here is the current smb.conf:

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "miller"
netbios name = "millerserver"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no
guest account = nobody
create mask = 0644
directory mask = 0755


#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700

[Storage]
        comment = ITunes
        path = /media/Storage/
        public = yes
        guest ok = yes
        writeable = yes
        read only = No

---

### Post by albinootje on 2009-01-05
> 
/dev/sdb1 on /media/Storage type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

Ok, I just tested with a NTFS partition on an usb stick, mounting with -o uid=1000 doesn't show that in the mount output.
Well. I don't see what it wouldn't work now, I'll test it with samba on my desktop soonish.

---

### Post by albinootje on 2009-01-05
I just tested it with a NTFS partition here on some usb-stick.

Mounted like this :
mount /dev/sdb1 /tmp/test -t ntfs-3g -o uid=1000,gid=1000,umask=000

> 
test share section in /etc/samba/smb.conf :
[TEST]
   comment = TEST
   read only = No
   writable = yes
#   locking = no
   path = /tmp/test
   guest ok = yes


> 
$ testparm 
Load smb config files from /etc/samba/smb.conf
Processing section "[TEST]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[TEST]
	comment = TEST
	path = /tmp/test
	read only = No
	guest ok = Yes


Tried with my user which has uid 1000, and i could create a new directory.
Also anonymous access let me create a new directory.

---

### Post by grossinm on 2009-01-05
grossinm@millerserver:~$ sudo umount /dev/sdb1
grossinm@millerserver:~$ sudo mount /dev/sdb1 /media/Storage -t ntfs-3g -o uid=1000,gid=1000,umask=000
grossinm@millerserver:~$ sudo nano smb.conf
grossinm@millerserver:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                                              [ OK ] 
 * Starting Samba daemons                                                                              [ OK ] 
grossinm@millerserver:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[grossinm]"
Processing section "[Storage]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = MILLER
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[grossinm]
	path = /home/grossinm
	read only = No
	guest ok = Yes

[Storage]
	path = /media/Storage
	guest ok = Yes
grossinm@millerserver:~$ smbclient //localhost/Storage/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> ls
  .                                   D        0  Mon Jan  5 10:56:30 2009
  ..                                  D        0  Mon Jan  5 16:05:28 2009
  System Volume Information           D        0  Mon Jan  5 10:56:30 2009

		59616 blocks of size 16777216. 59610 blocks available
smb: \> mkdir test
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test
smb: \> 

So close.  The permissions for the Storage share are still w/ Grossinm.  The permissions for the media section are still w/ Root though...

Also, found this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224317]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224317")

---

### Post by grossinm on 2009-01-05
Rightly or wrongly, I am reformatting the drive to Ext3 and will see if that makes any difference....

---

### Post by grossinm on 2009-01-05
No change, and now the permissions are set back to Root on Storage...

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> No change, and now the permissions are set back to Root on Storage...

With ext3 it should be much easier.
Then you can properly set the permissions permanently without any extra mount options.

---

### Post by grossinm on 2009-01-06
Well, it is ready to mount, but after trying last night to figure out the appropriate mount command, I have not had any luck. Should I just sudo mount /dev/sdb1 /media/Storage  ?

---

### Post by grossinm on 2009-01-06
Ok, so I tried this:

grossinm@millerserver:~$ sudo umount /dev/sdb1
[sudo] password for grossinm: 
umount: /dev/sdb1: not mounted
grossinm@millerserver:~$ chown -R grossinm /media/Storage
chown: changing ownership of `/media/Storage': Operation not permitted
grossinm@millerserver:~$ sudo chown -R grossinm /media/Storage
grossinm@millerserver:~$ sudo mount /dev/sdb1 /media/Storage
grossinm@millerserver:~$ 


When I CHOWN owned the folder (before mounting) it gave me read/write permissions.  However, when I mounted it, it went back to Root as the owner.  

And, as of right now, I can still only browse that folder, I cannot write to it via Samba or via the local file system.

---

### Post by grossinm on 2009-01-06
Ok, so I tried this:

grossinm@millerserver:~$ sudo umount /dev/sdb1
[sudo] password for grossinm: 
umount: /dev/sdb1: not mounted
grossinm@millerserver:~$ chown -R grossinm /media/Storage
chown: changing ownership of `/media/Storage': Operation not permitted
grossinm@millerserver:~$ sudo chown -R grossinm /media/Storage
grossinm@millerserver:~$ sudo mount /dev/sdb1 /media/Storage
grossinm@millerserver:~$ 


When I CHOWN owned the folder (before mounting) it gave me read/write permissions.  However, when I mounted it, it went back to Root as the owner.  

And, as of right now, I can still only browse that folder, I cannot write to it via Samba or via the local file system.

---

### Post by grossinm on 2009-01-06
So then I:

grossinm@millerserver:~$ sudo chown -R grossinm /media/Storage
grossinm@millerserver:~$ 

after it is mounted, and now I own it (grossinm) w/ full read write permissions. (I think).

But still cannot manage to write from Samba.  

let me restart the Samba server...no changes on samba restart.

Currently I can browse but cannot write to the folder.

---

### Post by grossinm on 2009-01-06
Ok, current status update:

grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/Storage type ext3 (rw)
grossinm@millerserver:~$ id
uid=1000(grossinm) gid=1000(grossinm) groups=4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare),1000(grossinm)
grossinm@millerserver:~$ ls -la /media
total 16
drwxr-xr-x  4 root     root       4096 2009-01-05 16:05 .
drwxr-xr-x 20 root     root       4096 2009-01-04 14:41 ..
lrwxrwxrwx  1 root     root          6 2009-01-04 13:59 cdrom -> cdrom0
drwxr-xr-x  2 root     root       4096 2009-01-04 13:59 cdrom0
-rw-r--r--  1 root     root          0 2009-01-05 16:03 .hal-mtab
-rw-------  1 root     root          0 2009-01-05 10:18 .hal-mtab-lock
drwxrwxrwx  4 grossinm grossinm 4096 2009-01-06 07:20 Storage
grossinm@millerserver:~$ 

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "miller"
netbios name = "millerserver"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no
guest account = nobody
create mask = 0644
directory mask = 0755
unix extensions = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700

[Storage]
        comment = ITunes
        path = /media/Storage
        # locking = no
        guest ok = yes
        writeable = yes
        read only = No
        force user = grossinm
        force group = grossinm

more info:

grossinm@millerserver:~$ dmesg | tail
[   26.097043] [drm] Initialized drm 1.1.0 20060810
[   26.108881] pci 0000:01:00.0: setting latency timer to 64
[   26.109130] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   26.487299] [drm] Setting GART location based on new memory map
[   26.488693] [drm] Loading R300 Microcode
[   26.488739] [drm] Num pipes: 1
[   26.488775] [drm] writeback test succeeded in 1 usecs
[   33.644511] eth0: no IPv6 routers present
[  368.944023] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[  421.944022] usb 5-4: reset high speed USB device using ehci_hcd and address 3


And still, after all of this, I am getting Access denied from Samba client's who try to write to the Storage (and it's heirs) folder.  Do I need to own the Media folder as well?

Just to be clear, I am connecting from the remote machines as grossinm (and password).  not anonymously.

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> Well, it is ready to mount, but after trying last night to figure out the appropriate mount command, I have not had any luck. Should I just sudo mount /dev/sdb1 /media/Storage  ?

Yes, that's correct for ext3.
But with ext3 you should realise/remember that by default only root (the sysadmin account) can write to it.
So.. create a new directory on it, and give your samba user full access.
For example :
```

sudo mount /dev/sdb1 /media/Storage
sudo mkdir /media/Storage/test
sudo chown -R 1000:1000 /media/Storage/test

```
Where 1000 is the uid and gid for your preferred samba user.

By the way, I've tested the system-config-samba GUI config app. 
It worked, but only after manually correcting the permissions for the share!

---

### Post by grossinm on 2009-01-06
Ok, following another lead now (for anyone still reading anyhow).  Edited FSTAB to add this line:

# Entry for /dev/sdb1:
UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391 /media/Storage ext3 defaults 0 0


Mount output reads:
grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdf1 on /media/Storage_ type ext3 (rw,nosuid,nodev,uhelper=hal)
grossinm@millerserver:~$ 


I now have a Storage and Storage_ in my file system.  I believe I have some type of conflict happening due to the FSTAB entry, but it does not appear to have any affect to the system.

the Samba shared drive is the Storage folder (established by smb.conf????)  the new folder, Storage_ is not shared.

Suicidal thoughts are beginning to creep in to this endeavor

---

### Post by grossinm on 2009-01-06
Albinootje,  as you can see I started experimenting.  Right now, /dev/sdb1 does not exist (see terminal output):

grossinm@millerserver:~$ sudo mount /dev/sdb1 /media/Storage
mount: special device /dev/sdb1 does not exist
grossinm@millerserver:~$ 

Should I remove the FSTAB entry, or should I start using the FSTAB assigned location of /dev/sdf1  ???  Is it a good idea to have the FSTAB entry?

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> 
the Samba shared drive is the Storage folder (established by smb.conf????)  the new folder, Storage_ is not shared.

Suicidal thoughts are beginning to creep in to this endeavor

Let's slow down a little, have some patience.
There are hundreds of people here who can possibly help you, but perhaps not everyone has enough time right now.
I have some more time in about 3 or 4 hours. Hang on. 
Don't give up, you must be pretty close to the solution now.

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> Albinootje,  as you can see I started experimenting.  Right now, /dev/sdb1 does not exist (see terminal output):

grossinm@millerserver:~$ sudo mount /dev/sdb1 /media/Storage
mount: special device /dev/sdb1 does not exist
grossinm@millerserver:~$ 

Should I remove the FSTAB entry, or should I start using the FSTAB assigned location of /dev/sdf1  ???  Is it a good idea to have the FSTAB entry?

Can you post the output of the following :
```

lsusb
mount
dmesg|tail -n50

```

In your case it makes sense to have the /etc/fstab entry I think, but I don't know for sure whether the auto mounting of removable data does follow the entries in /etc/fstab.

---

### Post by grossinm on 2009-01-06
No worries.  Thank you for the help.  I'll try not to botch the system up anymore (well, maybe a little) until I hear some more ideas/guidance.

---

### Post by grossinm on 2009-01-06
Terminal output:

grossinm@millerserver:~$ lsusb
Bus 005 Device 003: ID 055d:3020 Samsung Electro-Mechanics Co. 
Bus 005 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdf1 on /media/Storage_ type ext3 (rw,nosuid,nodev,uhelper=hal)

grossinm@millerserver:~$ dmesg | tail -n50
[   15.745456] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.496043] intel8x0_measure_ac97_clock: measured 55200 usecs
[   16.496051] intel8x0: clocking to 48000
[   17.205861]  sdf1
[   17.207188] sd 4:0:0:0: [sdf] Attached SCSI disk
[   17.208416] sd 4:0:0:0: Attached scsi generic sg6 type 0
[   18.007347] lp: driver loaded but no devices found
[   18.263959] Adding 1502036k swap on /dev/sda7.  Priority:-1 extents:1 across:1502036k
[   18.833398] EXT3 FS on sda6, internal journal
[   20.210939] type=1505 audit(1231258033.371:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4107
[   20.211173] type=1505 audit(1231258033.371:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4107
[   20.390204] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.979244] NET: Registered protocol family 10
[   20.980474] lo: Disabled Privacy Extensions
[   20.982638] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.777557] ACPI: WMI: Mapper loaded
[   22.730218] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   22.877352] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   22.877361] apm: disabled - APM is not SMP safe.
[   23.078491] ppdev: user-space parallel port driver
[   23.804160] b44: eth0: Link is up at 100 Mbps, full duplex.
[   23.804168] b44: eth0: Flow control is off for TX and off for RX.
[   23.804297] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.792981] Bluetooth: Core ver 2.13
[   24.793438] NET: Registered protocol family 31
[   24.793447] Bluetooth: HCI device and connection manager initialized
[   24.793454] Bluetooth: HCI socket layer initialized
[   24.816845] Bluetooth: L2CAP ver 2.11
[   24.816854] Bluetooth: L2CAP socket layer initialized
[   24.841163] Bluetooth: SCO (Voice Link) ver 0.6
[   24.841172] Bluetooth: SCO socket layer initialized
[   24.858472] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.858482] Bluetooth: BNEP filters: protocol multicast
[   24.884478] Bridge firewalling registered
[   24.885206] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   24.959905] Bluetooth: RFCOMM socket layer initialized
[   24.961560] Bluetooth: RFCOMM TTY layer initialized
[   24.961572] Bluetooth: RFCOMM ver 1.10
[   26.609301] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.804706] [drm] Initialized drm 1.1.0 20060810
[   26.816308] pci 0000:01:00.0: setting latency timer to 64
[   26.816563] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   27.194670] [drm] Setting GART location based on new memory map
[   27.196079] [drm] Loading R300 Microcode
[   27.196116] [drm] Num pipes: 1
[   27.196127] [drm] writeback test succeeded in 1 usecs
[   34.168512] eth0: no IPv6 routers present
[  116.405007] kjournald starting.  Commit interval 5 seconds
[  116.407309] EXT3 FS on sdf1, internal journal
[  116.407326] EXT3-fs: mounted filesystem with ordered data mode.
grossinm@millerserver:~$

---

### Post by sd23ddde on 2009-01-06
> **grossinm said:**
> 
grossinm@millerserver:~$ sudo mount /dev/sdb1 /media/Storage
mount: special device /dev/sdb1 does not exist
grossinm@millerserver:~$ 

This just means that the drive is not linked to /dev/sdb1 ... you might have a look if you find a /dev/sdc1 or sth simmilar (mayby ubuntu just "switched" the assignment).


> **grossinm said:**
> 
Should I remove the FSTAB entry, or should I start using the FSTAB assigned location of /dev/sdf1  ???  Is it a good idea to have the FSTAB entry?
The best is using the UUIDs since the mappings always will be fine even if your drive gets another shortcut. With the UUIDs ubuntu doesn't have to care about sda? / sdb? it just uses the UUID from your harddrive. So I would suggest leaving it as it was.

Please tell me if I'm right: 
the system is mounting your drive but you + your samba have no privileges on the mount-point. if YOU mount the drive manually at least you can access it properly while being remote connected. 

Now the question: If you mounted it manually, are you able to access it with your user remotely? or is this not possible?

Kind regards

---

### Post by grossinm on 2009-01-06
The current situation right now is this:

xubuntu 8.10 up and running on Dell Dimension.  512mb Ram, 2.8 ghz processor and a 40gb internal drive.

Samba is sharing the home directory (grossinm) which I can connect to, browse and r/w.

Samba is also sharing a USB  attached 1TB Western Digital My Book.  I can browse to the drive, I can read from the drive, _but I cannot write to the drive_.

Also, at this point, I have two different Storage folders (one called Storage and one called Storage_ (and I just had another Storage folder appear inside the Storage folder, can you say twilight zone?)

Thanks,

Greg

---

### Post by albinootje on 2009-01-06
Using UUID is indeed a good idea for this setup.
If you have the drive attached, please type :
```

blkid

```
to find out the UUID.

---

### Post by sd23ddde on 2009-01-06
just to complete this: you formated your drive in ext3 instead of NTFS right?

@albinootje: I guess he already has the UUID in the FSTAB, referencing to his previous post:

# Entry for /dev/sdb1:
UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391 /media/Storage ext3 defaults 0 0

kind regards

---

### Post by sd23ddde on 2009-01-06
> **sd23ddde said:**
> **just to complete this: you formated your drive in ext3 instead of NTFS right?**

@albinootje: I guess he already has the UUID in the FSTAB, referencing to his previous post:

# Entry for /dev/sdb1:
UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391 /media/Storage **ext3** defaults 0 0

kind regards

I guess I answered my question with my own post ^^ sorry

kind regards

---

### Post by grossinm on 2009-01-06
grossinm@millerserver:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="21caa10a-e2cc-466c-80a8-4223355e4073" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="caf62bd1-914f-4349-ab34-02d3cd534f36" 
/dev/sda6: UUID="d241f308-a265-463f-8ffa-8275cdaecf96" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="97bdb42b-6e32-4169-99aa-f127f201a02b" 
/dev/sdb1: LABEL="Storage" UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391" SEC_TYPE="ext2" TYPE="ext3" 
grossinm@millerserver:~$

---

### Post by grossinm on 2009-01-06
> **sd23ddde said:**
> I guess I answered my question with my own post ^^ sorry

kind regards

I do that all the time... :cool:

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> grossinm@millerserver:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="21caa10a-e2cc-466c-80a8-4223355e4073" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="caf62bd1-914f-4349-ab34-02d3cd534f36" 
/dev/sda6: UUID="d241f308-a265-463f-8ffa-8275cdaecf96" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="97bdb42b-6e32-4169-99aa-f127f201a02b" 
/dev/sdb1: LABEL="Storage" UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391" SEC_TYPE="ext2" TYPE="ext3" 
grossinm@millerserver:~$

OK, sorry, I didn't read this properly before :( 
You already have it in /etc/fstab, and correctly! :)

---

### Post by sd23ddde on 2009-01-06
I just found a hint on using pmount instead of fstab for removable-devices in this thread: [http://ubuntuforums.org/showthread.php?t=482796]("http://ubuntuforums.org/showthread.php?t=482796")

Also you might have a look on this thread (also linked in the thread before):  [http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

You might give it a try mounting the Storage with
```

pmount /dev/sdb1 Storage

```
pmount will automatically mount the "Storage" in "media" since pmount doesn't mount anywhere else than in media ;)

kind regards

---

### Post by grossinm on 2009-01-06
Ok, so before I start hacking away, I should:
 
[LIST=1]
[*]Remove the FSTAB entry
[*]Run PMOUNT from terminal?
[/LIST]

Is there a way to set up so that PMOUNT runs on  boot / reboot?

Good find by the way!

---

### Post by grossinm on 2009-01-06
Ok, I went ahead and removed the FSTAB entry, rebooted and ran BLKID:
grossinm@millerserver:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="21caa10a-e2cc-466c-80a8-4223355e4073" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="caf62bd1-914f-4349-ab34-02d3cd534f36" 
/dev/sda6: UUID="d241f308-a265-463f-8ffa-8275cdaecf96" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="97bdb42b-6e32-4169-99aa-f127f201a02b" 
/dev/sdb1: LABEL="Storage" UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391" SEC_TYPE="ext2" TYPE="ext3" 

I then went ahead and ran pmount as shown below:

grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Storage
[sudo] password for grossinm: 
Error: device /dev/sdb1 is not removable
grossinm@millerserver:~$ 

So, why does it show as being "not removable" (btw, I just removed it and threw it across the room! :cool:)

also, ran Mount:

grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by sd23ddde on 2009-01-06
exactly right
1 remove the fstab entry 
2 write a small little sh script that runs the pmount.

for making your script being automatically executed after / while reboot, you have to do the following:

1 move your script to the init.d (/etc/init.d) folder
```
sudo gedit /etc/init.d/your_script
```
2 make the file executable 
```
sudo chmod +x /etc/init.d/your_script
```
3 make it run on boot 
```
sudo update-rc.d my_script defaults
```

good luck + kind regards

---

### Post by sd23ddde on 2009-01-06
> **grossinm said:**
> 

grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Storage
[sudo] password for grossinm: 
Error: device /dev/sdb1 is not removable
grossinm@millerserver:~$ 

So, why does it show as being "not removable" (btw, I just removed it and threw it across the room! :cool:)

ok... thats not what it was supposed to do... "not removable" hu?!... its a little dirty hack, but try adding a line to /etc/pmount.allow with your drive
```
/dev/sdb1
```
and retry it.

---

### Post by grossinm on 2009-01-06
gedit is the same as Nano?  (text editors under terminal?)

So when I exit Nano, it will save to /etc/inid.d/myscriptname

Run the chmod at the command line to allow it to be executed, 

And the last command line updates a file which executes scripts at boot?

Got all that, and will do, however, still have the "not removable" issue.

Thank you.

---

### Post by grossinm on 2009-01-06
Ok, so I added it to the pmount.allow and ran the following:

grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Storage
[sudo] password for grossinm: 
Error: device /dev/sdb1 is not removable
grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
grossinm@millerserver:~$ sudo nano /etc/pmount
grossinm@millerserver:~$ sudo nano /etc/pmount.allow
grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Storage
Error: directory /media/Storage is not empty
grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Storage
Error: device /dev/sdb1 is already mounted to /media/Storage_
grossinm@millerserver:~$ umount /dev/sdb1
grossinm@millerserver:~$ sudo pmount -w /dev.sdb1 Storage
Error: could not determine real path of the device: No such file or directory
grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Storage
Error: directory /media/Storage is not empty
grossinm@millerserver:~$ umount /dev/sdb1
grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Storage
grossinm@millerserver:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="21caa10a-e2cc-466c-80a8-4223355e4073" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="caf62bd1-914f-4349-ab34-02d3cd534f36" 
/dev/sda6: UUID="d241f308-a265-463f-8ffa-8275cdaecf96" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="97bdb42b-6e32-4169-99aa-f127f201a02b" 
/dev/sdb1: LABEL="Storage" UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391" SEC_TYPE="ext2" TYPE="ext3" 
grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/Storage type ext3 (rw,noexec,nosuid,nodev,errors=continue)


Basically, I had to mount the drive, delete the contents, and then PMount let me "mount" the drive.  However, I still do not have the ability to write to the drive, and it looks like it is still mounted under mount and not pmount???

Did I miss something here?

---

### Post by sd23ddde on 2009-01-06
gedit / nano / vi / vim are all common editors
Im not sure about nano (vi / vim user) but I think you have to exit via CTRL + X and than the file will be saved, yes.

The last command adds your script to the bootsequence so it will be run on every startup.

Back to the problem. Pmount tries to create the folder you tell him to mount on. If "Storage" already exists (but is empty) pmount should mount there without any problem.

please go for:
```

umount /dev/sdb1
pumount /dev/sdb1

```

and afterwards try to pmount it again.

kind regards

---

### Post by grossinm on 2009-01-06
UPMount not recoginzed:

grossinm@millerserver:~$ upmount /dev/sdb1
bash: upmount: command not found

So, I then tried:

grossinm@millerserver:~$ sudo pmount -w /dev/sdb1 Music
grossinm@millerserver:~$ sudo nano smb.conf
grossinm@millerserver:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                [ OK ] 
 * Starting Samba daemons                                                [ OK ] 

This created a new folder in media/Music (with a folder called Test in it).  I then edited my smb.conf to change the path for the share to /media/Music and restarted Samba.

So, there is still a Storage folder.  I cannot delete it or unmount it at this point.  I have a music folder, but it is not being shared by Samba.

...hmm....

---

### Post by sd23ddde on 2009-01-06
I had a misspelling in the command. its "pumount" not "upmount". As long as the pmount is active you can't delete the Storage folder.

With the Music folder try to set the chmod to 777 (just for testing) and chown to root:root

kind regards

---

### Post by grossinm on 2009-01-06
I have a few things going on now:

PUMOUNT /dev/sdb1.  This unmounted the Music folder, and it disappeared.  That is fine.

I still have Storage2 folder and cannot delete it, nor can I figure out how to PUMOUNT it, since Music essentially took its place as /dev/sdb1.  Can I PUMOUNT /dev/sdb1 Storage2  ???

I also ran BLKID:

grossinm@millerserver:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="21caa10a-e2cc-466c-80a8-4223355e4073" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="caf62bd1-914f-4349-ab34-02d3cd534f36" 
/dev/sda6: UUID="d241f308-a265-463f-8ffa-8275cdaecf96" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="97bdb42b-6e32-4169-99aa-f127f201a02b" 
/dev/sdb1: LABEL="Storage" UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391" SEC_TYPE="ext2" TYPE="ext3"

It still shows /dev/sdb1 as Storage (and I can see see this on my clients, but cannot browse it as it does not exist).

I have a feeling I need to do a little house keeping before I try and move any further forward (backward????)

Greg

---

### Post by sd23ddde on 2009-01-06
sorry grossinm,
I have to skip for about 1-2 hours to take care of my son. I'll be back then, but hopefully you might have solved the problem till then.

good luck!
kind regards

---

### Post by sd23ddde on 2009-01-06
you can pumount everything that was pmounted before!

kind regards

---

### Post by sd23ddde on 2009-01-06
you can pumount everything that was pmounted before!

kind regards

---

### Post by grossinm on 2009-01-06
Status Update:

grossinm@millerserver:~$ blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="21caa10a-e2cc-466c-80a8-4223355e4073" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="caf62bd1-914f-4349-ab34-02d3cd534f36" 
/dev/sda6: UUID="d241f308-a265-463f-8ffa-8275cdaecf96" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="97bdb42b-6e32-4169-99aa-f127f201a02b" 
**/dev/sdb1: LABEL="Storage" UUID="e6577b11-4c95-4a12-a7eb-31f6c5e1a391" SEC_TYPE="ext2" TYPE="ext3" **

grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)

grossinm@millerserver:~$ dmesg | tail
[   25.872500] [drm] Initialized drm 1.1.0 20060810
[   25.884146] pci 0000:01:00.0: setting latency timer to 64
[   25.884406] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   26.254215] [drm] Setting GART location based on new memory map
[   26.255593] [drm] Loading R300 Microcode
[   26.255640] [drm] Num pipes: 1
[   26.255650] [drm] writeback test succeeded in 1 usecs
[   33.584513] eth0: no IPv6 routers present
[  386.940031] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[  469.944022] usb 5-4: reset high speed USB device using ehci_hcd and address 3

grossinm@millerserver:~$ id
uid=1000(grossinm) gid=1000(grossinm) groups=4(adm),20(dialout),24(cdrom),46(plugdev),112(lpadmin),120(admin),122(sambashare),1000(grossinm)

grossinm@millerserver:~$ ls -la /media
total 12
drwx------  3 grossinm grossinm 4096 2009-01-06 11:38 .
drwxr-xr-x 20 root     root     4096 2009-01-04 14:41 ..
lrwxrwxrwx  1 grossinm root        6 2009-01-04 13:59 cdrom -> cdrom0
drwx------  2 grossinm grossinm 4096 2009-01-04 13:59 cdrom0
-rw-r--r--  1 root     root        0 2009-01-06 11:38 .hal-mtab

grossinm@millerserver:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 055d:3020 Samsung Electro-Mechanics Co. 
Bus 005 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
grossinm@millerserver:~$ 

Current smb.conf (I removed the share Storage and music and will add back later).  I'm not sure that Samba is the problem...:

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "miller"
netbios name = "millerserver"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no
guest account = nobody
create mask = 0644
directory mask = 0755
unix extensions = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700

This is sharing the home directory just fine (perhaps I should just get a TB drive to install xubuntu onto ...)

I am now going to try to:

Sudo PMount -w /dev/sdb1 MD1
sudo CHOWN -R grossinm /media/MD1

Should also do something w/ CHMOD, but I'm familiar enough w/ that one....

I'll then try to reimplement the Samba share of the folder MD1.

one thing, the "storage" folder I started out with seems to be hangin around (in BLKID, and shows up on client machines, but not browsable).  Is there a cache file halting any progress I might be making?

---

### Post by sd23ddde on 2009-01-06
hiho, back again...

regarding the "lazy" Storage, try to do a "umount -l". That should umount the drive asap. If it is not possible to be umounted saying "drive is busy" you might have a look on whats going on via ```
lsof | grep '/media/Storage
```
That should list every process that is still digged in to the mounted device.

Since "Storage" is not in the "mount" list you might try on "pumount /dev/sdb1" or "pumount -l /dev/sdb1" this should help.

If the "Storage" share is still visible for other PCs it definatly is a samba problem (maybe stop / start smb?).

kind regards

---

### Post by grossinm on 2009-01-06
I was able to take control of the Storage2 folder via CHOWN, and then deleted it.

I implemented the changes at the end of my previous post, but I do not seem to be sharing MD1 via Samba.  Not sure why.  here is my updated smb.conf:

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "miller"
netbios name = "millerserver"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* $
obey pam restrictions = yes
pam password change = no
null passwords = no
guest account = nobody
create mask = 0644
directory mask = 0755
unix extensions = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700

[myfiles]
        comment = shared files backups
        path = /media/MD1
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700

I tried logging into MD1 locally, but no luck:

grossinm@millerserver:~$ sudo nano smb.conf
[sudo] password for grossinm: 
grossinm@millerserver:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                [ OK ] 
 * Starting Samba daemons                                                [ OK ] 
grossinm@millerserver:~$ smbclient //localhost/MD1
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
grossinm@millerserver:~$ smbclient //localhost/MD1/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
grossinm@millerserver:~$ 

in my xubuntu Gui, there seems to be an issue, because under places, I still Storage, and when I click on it, it takes me to MD1 folder.

Also, tried logging into Storage via Samba, no luck, but could get into my home directory:

grossinm@millerserver:~$ smbclient //localhost/Storage/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
grossinm@millerserver:~$ smbclient //localhost/grossinm/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \>

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> 
[myfiles]
        comment = shared files backups
        path = /media/MD1
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700
-- cut --
grossinm@millerserver:~$ smbclient //localhost/MD1
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

Try with this instead :
```

smbclient //localhost/myfiles

```

---

### Post by sd23ddde on 2009-01-06
the MD1 problem should be solved as albinootje already said. The text you type in as "title" for every section is the name of the share so it is //localhost/**myfiles** instead of //localhost/**MD1**

If you deleted all the "Storage" stuff out of your smb.conf (as it looks like), the remaining "Storage" only seems to be a simple caching problem of the samba clients (as far as I can tell).

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> 
[myfiles]
        comment = shared files backups
        path = /media/MD1
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700


I just started testing with some usb-stick with ext3 on it, and.. I cannot write on it anonymously.. but with my samba user I can.

---

### Post by albinootje on 2009-01-06
> **albinootje said:**
> I just started testing with some usb-stick with ext3 on it, and.. I cannot write on it anonymously.. but with my samba user I can.

This is what I did (usb-stick is mounted in /media/disk-1) :
```

sudo mkdir /media/disk-1/Everything
sudo chown -R 1000:1000 /media/disk-1/Everything

```

Relevant part of the samba config :
```

[test]
	comment = Test
	path = /media/disk-1/Everything
	read only = No
	guest ok = Yes

```

---

### Post by grossinm on 2009-01-06
I fixed the Storage problem, by:

grossinm@millerserver:~$ pumount /dev/sdb1
grossinm@millerserver:~$ pmount -w /dev/sdb1 Storage
grossinm@millerserver:~$ sudo nano smb.conf
grossinm@millerserver:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                [ OK ] 
 * Starting Samba daemons                                                [ OK ] 

I edit the smb.conf file to this:

[Storage]
        comment = shared
        path = /media/Storage/
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700
        force user = grossinm
        force group = grossinm

I could then browse Storage via smbclient again, but not write.  

I will now try albinootje's suggetions:

grossinm@millerserver:~$ sudo mkdir /media/Storage/everything
grossinm@millerserver:~$ sudo chown -R 1000:1000 /media/Storage/everything
grossinm@millerserver:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                [ OK ] 
 * Starting Samba daemons                                                [ OK ] 
grossinm@millerserver:~$ smbclient //localhost/everything/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
grossinm@millerserver:~$ smbclient //localhost/Storage/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> ls
  .                                   D        0  Tue Jan  6 13:48:48 2009
  ..                                  D        0  Tue Jan  6 13:40:42 2009
  everything                          D        0  Tue Jan  6 13:48:48 2009
  Test                                D        0  Tue Jan  6 10:44:01 2009
  .Trash-1000                        DH        0  Tue Jan  6 07:46:14 2009

		58681 blocks of size 16777216. 55687 blocks available
smb: \> mkdir test2
NT_STATUS_MEDIA_WRITE_PROTECTED making remote directory \test2
smb: \> ls -la
NT_STATUS_NO_SUCH_FILE listing \-la

		58681 blocks of size 16777216. 55687 blocks available
smb: \> quit
grossinm@millerserver:~$ ls -la /media
total 16
drwx------  4 grossinm grossinm   4096 2009-01-06 13:40 .
drwxr-xr-x 20 root     root       4096 2009-01-04 14:41 ..
lrwxrwxrwx  1 grossinm root          6 2009-01-04 13:59 cdrom -> cdrom0
drwx------  2 grossinm grossinm   4096 2009-01-04 13:59 cdrom0
-rw-r--r--  1 root     root          0 2009-01-06 11:38 .hal-mtab
drwx------  5 grossinm sambashare 4096 2009-01-06 13:48 Storage
grossinm@millerserver:~$ ls -la /media
total 16
drwx------  4 grossinm grossinm 4096 2009-01-06 13:40 .
drwxr-xr-x 20 root     root     4096 2009-01-04 14:41 ..
lrwxrwxrwx  1 grossinm root        6 2009-01-04 13:59 cdrom -> cdrom0
drwx------  2 grossinm grossinm 4096 2009-01-04 13:59 cdrom0
-rw-r--r--  1 root     root        0 2009-01-06 11:38 .hal-mtab
drwx------  5 grossinm grossinm 4096 2009-01-06 13:48 Storage
grossinm@millerserver:~$ 
 
smb.conf is now:

[Storage]
        comment = test
        path = /media/Storage/everything
        read only = No
        guest ok = Yes

So, still unable to write to the drive.  Also, when I smbclient into Storage, it still drops me at /media/Storage and not at /media/Storage/everything  

It appears that restarting the samba client is not enabling the changes I am making (so I am stuck with Storage and /media/Storage

Greg

---

### Post by sd23ddde on 2009-01-06
for me (again) it looks like a problem with samba...
with my USB-Drive (NTFS) I have the following smb configuration:

```

[share]
  comment = shared folder
  path = /mnt/sda1/share
  browsable = yes
  directorymask = 777
  read only = No
  valid users = sd23, root, samba
  admin users = sd23, root, samba

```

this is working without any problem. Maybe it is something about the guest-user and the user-specs in your general part? (never tried that).

kind regards


PS: I'm off for today, I hope you can find the error... I'm back tomorrow!

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> 
[Storage]
        comment = shared
        path = /media/Storage/
--- cut ---

grossinm@millerserver:~$ smbclient //localhost/Storage/
Enter grossinm's password: 
Domain=[MILLERSERVER] OS=[Unix] Server=[Samba 3.2.3]
smb: \> ls
  .                                   D        0  Tue Jan  6 13:48:48 2009
  ..                                  D        0  Tue Jan  6 13:40:42 2009
  everything                          D        0  Tue Jan  6 13:48:48 2009


The difference with my test example is "everything" ;-)
Please try this in your smb.conf :

```

[Storage]
        comment = shared
        path = /media/Storage/everything

```
Restart samba after that, and try again :)

---

### Post by grossinm on 2009-01-06
Ok, so since everyone's USB sticks are working, I got out an old Ipod Shuffle, reformatted it FAT32 and put it into the machine.

It is mounted under /media/NVOL

Here is the smb.conf:

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "miller"
netbios name = "millerserver"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* $
obey pam restrictions = yes
pam password change = no
null passwords = no
guest account = nobody

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writeable = yes
        security mask = 0700
        create mask = 0700

[Storage]
        comment = shared
        path = /media/Storage/everything
        read only = No
        guest ok = Yes

[NVol]
        comment =atest
        path = /media/NVOL/
        read only = No
        guest ok = Yes

I restarted Samba, and the share is no where to be found.  Device is shown in the mount command:

grossinm@millerserver:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/Storage type ext3 (rw,noexec,nosuid,nodev,errors=continue)
/dev/sdg2 on /media/PATCHSTICK_ type hfsplus (rw,nosuid,nodev,uhelper=hal)
/dev/sdg1 on /media/Recovery_ type hfsplus (rw,nosuid,nodev,uhelper=hal)
/dev/sdh1 on /media/NVOL type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)

At this point, I am inclined to start this whole thing over!  Reload samba etc...  Should I step back from the edge, or move closer?

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> Ok, so since everyone's USB sticks are working, 

So.. your Storage share is now read/write for your samba user ? Right ?
> 
I got out an old Ipod Shuffle, reformatted it FAT32 and put it into the machine.
--- cut ---
/dev/sdg2 on /media/PATCHSTICK_ type hfsplus (rw,nosuid,nodev,uhelper=hal)
/dev/sdg1 on /media/Recovery_ type hfsplus (rw,nosuid,nodev,uhelper=hal)
/dev/sdh1 on /media/NVOL type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)

I have no experiences with ipods at all, but you have 3 partitions from it mounted it seems.

By the way, i've also testing the right-click "Share Options" inside the file manager (Nautilus).
When I used that, and wanted to give everyone access it simply did a chmod 1777 on my /media/disk-1/ directory.
Can you play with Nautilus share options with your ipod a bit ?

Starting a new thread with the title "Ipod sharing via Samba troubles" sounds like a wise idea.

---

### Post by grossinm on 2009-01-06
I tried to install Nautilus the yesterday, and it messed up my desktop, and since then I have not used it (may have uninstalled it).

Nope, still cannot write to my Storage share.  everything folder is inside of it, and I cannot write there either.  I can browse no problem though.

on the IPod.  I originally put it in before formatting, and those partions were there.  I've since deleted them, but they continue to show up in Mount.  Why is that?  I feel like anything I do to this machine is set in stone, w/o a way to remove it....

What is the correct CHMOD syntax and will give that a try?  Thank you.

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> I tried to install Nautilus the yesterday, and it messed up my desktop, and since then I have not used it (may have uninstalled it).

Ah.. I see. I forgot that you're using Xubuntu.
> 

Nope, still cannot write to my Storage share.  everything folder is inside of it, and I cannot write there either.  I can browse no problem though.

Very weird :(

---

### Post by grossinm on 2009-01-06
What should I be using?  I'm a bit afraid to lose the GUI, but this machine is about stability, so, if I should kick Xubuntu to the curb, I will...

I'm downloading Ubuntu Server 8.10 now and will proceed with installing that shortly (unless I hear otherwise).

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> What should I be using?  I'm a bit afraid to lose the GUI, but this machine is about stability, so, if I should kick Xubuntu to the curb, I will...

I didn't mean to suggest that Xubuntu is not OK. I just forgot for a moment that Nautilus does bring wallpaper + icons when used in another environment (DE or windowmanager) than in Gnome.

And I'm sorry to read that your file sharing with the external disks are still not working well :(

And I wondered about your samba users made in webmin (you created them in webmin's samba module, no ?). 
Did you give those samba users there certain privileges or ... ?
(It's years ago I used webmin for samba configurations, but I remember that it had quite some options).

---

### Post by grossinm on 2009-01-06
The user was created using the scrip in the smb.conf file at the first login...

---

### Post by grossinm on 2009-01-06
Ubuntu Server 8.10 up and running.

Is there a GUI???

Time to learn some more...

Ok, installed GNome....

So, now, to get Samba running, and then share the External Drive....need some coffee first

---

### Post by albinootje on 2009-01-06
> **grossinm said:**
> Ubuntu Server 8.10 up and running.

Is there a GUI???

No, but you are free to run the following :
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
which probably makes things easier.

---

### Post by grossinm on 2009-01-06
If your still there, here is where I am at:

installed Ubuntu 8.10
installed Gnome

 configured static IP address on internal network (read that was good for a file server).

Samba installed during installation.  So configured /etc/samba/smb.conf as follows:

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "miller"
netbios name = "mserver"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
#Share Definitions

[homes]
comment = Home Directories
browseable = yes
writable = yes
security mask = 0700
create mask = 0700

Restart samba and added grossinm as user (with password).

As of right now, I am trying to configure VNC (using x11VNC, no luck), and trying to get Samba running, no luck (actaully, I can log in locally using smbclient //localhost/homes/, but cannot see it on my network...

---

### Post by albinootje on 2009-01-07
> **grossinm said:**
> 
As of right now, I am trying to configure VNC (using x11VNC, no luck), and trying to get Samba running, no luck (actaully, I can log in locally using smbclient //localhost/homes/, but cannot see it on my network...

Is the "workgroup" the same ?

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by grossinm on 2009-01-07
Where do I find the "workgroup" inside Ubuntu?

Ok, it likes the workgroup is only configured in Samba.  so for now I am using Workgroup.

---

