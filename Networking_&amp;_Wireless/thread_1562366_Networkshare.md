---
title: "Networkshare"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by Elboully on 2010-08-27
Ok, so i have a networkshare. (named Netstoragewd). Since i'm a n00b, but willing to learn, i've followed a few tut's on the net, but nothing seems to help.
I'm not able to mount the networkshare on my Ubuntu machine. (Lucid Lynx).

The last tut i've followed is this: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

I know there's something i'm doing wrong, but i don't know what.
The goal is this: giving acces to read and write to a newly created group of users. And to mount the share ofcourse... :-)

The errors i'm getting are ranging from; unknown ip-adress (while i thouhgt that a name could do as well, no?) to an error something like this: 
error -1 (Unknown error 4294967295) opening credential file /home/tom.smbcredentials

If anyone can point me in the right direction, i'd be very glad. 
That way, i can learn from my mistakes and make progress.

Thx in advance!!

---

### Post by Elboully on 2010-08-31
Nobody with a little help pls?

---

### Post by bab1 on 2010-08-31
> **Elboully said:**
> Ok, so i have a networkshare. (named Netstoragewd). Since i'm a n00b, but willing to learn, i've followed a few tut's on the net, but nothing seems to help.
I'm not able to mount the networkshare on my Ubuntu machine. (Lucid Lynx).

The last tut i've followed is this: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

I know there's something i'm doing wrong, but i don't know what.
The goal is this: giving acces to read and write to a newly created group of users. And to mount the share ofcourse... :-)

The errors i'm getting are ranging from; unknown ip-adress (while i thouhgt that a name could do as well, no?) to an error something like this: 
error -1 (Unknown error 4294967295) opening credential file /home/tom.smbcredentials

If anyone can point me in the right direction, i'd be very glad. 
That way, i can learn from my mistakes and make progress.

Thx in advance!!

What is the file system type on the partition that holds the share?  Is it EXT or NTFS or ...?  From the terminal what is the the output of ```
mount
```

It would be useful to see the output of ```
less /etc/fstab
``` 

You can format the output by inserting the data between [code] [/code ] or use the [SIZE="3"]**#**[/SIZE] icon when in the *advanced *editing mode.

---

### Post by dmizer on 2010-08-31
> **Elboully said:**
> Ok, so i have a networkshare. (named Netstoragewd). Since i'm a n00b, but willing to learn, i've followed a few tut's on the net, but nothing seems to help.
I'm not able to mount the networkshare on my Ubuntu machine. (Lucid Lynx).

The last tut i've followed is this: [https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

I know there's something i'm doing wrong, but i don't know what.
The goal is this: giving acces to read and write to a newly created group of users. And to mount the share ofcourse... :-)

The errors i'm getting are ranging from; unknown ip-adress (while i thouhgt that a name could do as well, no?) to an error something like this: 
error -1 (Unknown error 4294967295) opening credential file /home/tom.smbcredentials

If anyone can point me in the right direction, i'd be very glad. 
That way, i can learn from my mistakes and make progress.

Thx in advance!!
The howto you used is quite old. Take a look at the second link in my sig.

---

### Post by Elboully on 2010-09-01
This is the output when the 'mount' command is given.

tom@Ubuntu-02:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

And here's the output of "less /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//Netstoragewd/public /media/public smbfs iocharset=utf8,credentials=/home/tom.smbcredentials,gid=1001 0 0

Can you guys tell me what i'm looking at? I already know that linux uses different partitions, fstab stands for FileSystemTable witch is used for mounting devices, but that's about it....

So thanks already for your help!!
Much appreciated!!

---

### Post by dmizer on 2010-09-01
The mount command is just telling us what file systems are mounted where. The /etc/fstab is telling us exactly what command you are using to mount your share.

What is the output of
```
sudo mount /media/public
```

This will show us some errors that we may be able to use in helping us solve your problem.

---

### Post by Elboully on 2010-09-02
tom@Ubuntu-02:~$ sudo mount /media/public
[sudo] password for tom: 
error -1 (Unknown error 4294967295) opening credential file /home/tom.smbcredentials
tom@Ubuntu-02:~$ 

This is the output when the mount /media/public is given.
I've already tried googling the error, but it doesn't make me any wiser.

---

### Post by dmizer on 2010-09-02
Looks like you have a problem with the permissions on your credentials file.

Lets see what the current permissions for your credentials file are:
```
sudo ls -la /home/tom/.smbcredentials
```

---

### Post by Elboully on 2010-09-04
Hello, sorry for replying a little later. This one had me going a bit. I couldn't find it in /home/tom. Instead i found it here, witch is, i presume, the root?

Output of command:

tom@Ubuntu-02:~$ ls -la .smbcredentials
-rwx------ 1 root root 35 2010-08-27 19:25 .smbcredentials

I've been doing some reading (the linux bible 2007) and found out that only root has read, write and execute permissions on the .smbcredentials? Shouldn't this be extended to other users to?

Thx already for the help!! Much appreciated.

---

### Post by dmizer on 2010-09-04
> **Elboully said:**
> Hello, sorry for replying a little later. This one had me going a bit. I couldn't find it in /home/tom. Instead i found it here, witch is, i presume, the root?

Output of command:

tom@Ubuntu-02:~$ ls -la .smbcredentials
-rwx------ 1 root root 35 2010-08-27 19:25 .smbcredentials

I've been doing some reading (the linux bible 2007) and found out that only root has read, write and execute permissions on the .smbcredentials? Shouldn't this be extended to other users to?

Thx already for the help!! Much appreciated.

Ah ha! I see your mistake now. You missed a / between tom and .smbcredentiials.
Change your /etc/fstab line to this ...
```
//Netstoragewd/public /media/public smbfs iocharset=utf8,credentials=/home/tom[COLOR="Red"]**/**[/COLOR].smbcredentials,gid=1001 0 0
```

---

### Post by Elboully on 2010-09-05
Thanks for the help on that one. I'd never see it if nobody pointed that one out to me. 
I've changed the /etc/fstab like you said, and now the drive is visible and accesible!!

Many thanks for all the help you've given!!!

On to the next problem.. .Lol

---

