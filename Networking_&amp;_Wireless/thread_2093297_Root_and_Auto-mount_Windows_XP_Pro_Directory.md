---
title: "Root and Auto-mount Windows XP Pro Directory?"
date: 2012-12-10
forum: Networking &amp; Wireless
---

### Post by jakfish on 2012-12-10
sudo mount.cifs //192.168.***.***/efile /mnt/efile -o user=domain\\username,pass=guest

That command works in console,, but I then have to put in my root password.  Then in File Manager, when in /mnt/efile, I have to "open current directory as root" to copy files to efile directory.

Is there any way to cut down the steps, to auto-mount /mnt/efile and auto-root, too?

Thanks,
Jake

---

### Post by dannyboy79 on 2012-12-10
are you truely in a domain environment or is this just a home network? is the username on your ubuntu box the same as the windows xp pro username? it appears like it's a permission issue. open a terminal and run the following commands and paste back the output

```
mount
```

```
ls -la /mnt/
```

```
ls -la /mnt/efile/
```

---

### Post by jakfish on 2012-12-10
Thank you for your quick reply.  I believe this is the pasting you asked for:


jake@S10-3t:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jake/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jake)
/dev/sdb1 on /media/DPUP type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda2 on /media/187A40D67A40B274 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
jake@S10-3t:~$ ls -la /mnt/
total 12
drwxr-xr-x  3 root root 4096 Nov 28 13:50 .
drwxr-xr-x 23 root root 4096 Dec  7 08:55 ..
drwxr-xr-x  2 root root 4096 Nov 28 13:50 efile
jake@S10-3t:~$ ls -la /mnt/efile/
total 8
drwxr-xr-x 2 root root 4096 Nov 28 13:50 .
drwxr-xr-x 3 root root 4096 Nov 28 13:50 ..

These commands were run *without* my usual command of:

sudo mount.cifs //192.168.***.***/efile /mnt/efile -o user=domain\\username,pass=guest

I don't believe I'm using a domain environment, merely a directory that is officially shared in XP Pro SP3.  I do not have an ubuntu box, and I do not have an ubuntu directory, ftp or otherwise, available to XP or anything else.

Again, I appreciate your help,
Jake

---

### Post by dannyboy79 on 2012-12-10
what do you mean you don't have an ubuntu box. aren't you using ubuntu and trying to mount the windows xp pro share called efile within ubuntu? Oh, you're running lubuntu, that's basically ubuntu with LXDE as the desktop manager

is the username within windows xp the same as the username on your ubuntu machine? first, run this command on the efile folder within /mnt/
```
sudo chown username:groupname /mnt/efile
```
replace username with YOUR username and groupname with YOUR username. Example if your username was bob: sudo chown bob:bob /mnt/efile

then try to mount it using the following
```
sudo mount -t cifs -o username=server_user,password=secret //server_IP/sharename /mnt/efile
```

---

### Post by jakfish on 2012-12-11
Thank you again for your help and my apologies for not yet knowing all the terminology; I'm new to Ubuntu, and mistakenly believe Ubuntu box was the OS running along something else.

This is successful:

sudo chown jake:jake /mnt/efile

So is this:

sudo mount -t cifs -o username=server_user,password=secret //192.168.***.***/efile /mnt/efile

However, there's not yet automation: even though the Windows share (efile) is anonymous/guest, I'm prompted for my root password, and to copy files to /efile in pcman, I must put in my root password again.

The user name of XP is BEAR, but with all devices,, I access the shared directory with 192.168.***.***/efile

Jake

---

### Post by dannyboy79 on 2012-12-11
lets see the ls -la command run on /mnt/ AFTER you mount the share.

```
ls -la /mnt/
```



Are you saying you're sharing the windows share and it's suppose to not require a password?

This is what I added to my /etc/fstab file so that it mounts automatically when I start the computer.
```
//192.168.0.39/public	/mnt/circle	cifs	auto,noexec,users,nounix,uid=1000,gid=1000,iocharset=utf8,username=daniel,password=password,file_mode=0777,dir_mode=0777,_netdev	0	0
```

---

### Post by jakfish on 2012-12-11
Yes, I have no password to the XP Pro shared folder.  It's an anonymous log-in.  Here is the paste you had asked to see, along with the initial mounting command:


jake@S10-3t:~$ sudo mount.cifs //192.168.***.***/efile /mnt/efile -o user=domain\\username,pass=guest
[sudo] password for jake: 
jake@S10-3t:~$ ls -la /mnt/
total 8
drwxr-xr-x  3 root root 4096 Nov 28 13:50 .
drwxr-xr-x 23 root root 4096 Dec  7 08:55 ..
drwxr-xr-x  1 root root    0 Dec 11 05:27 efile

---

### Post by jakfish on 2012-12-11
You did it.  Success.  I took your fstab command and doctored it:

//192.168.***.***/efile	/mnt/efile	cifs	auto,noexec,users,nounix,uid=1000,gid=1000,iocharset=utf8,username=guest,password=guest,file_mode=0777,dir_mode=0777,_netdev	0	0

Upon reboot, I had a mounted /mnt/efile in pcman with root access for file-copying to /mnt/efile

Anything else I should try before marking this thread as Solved?

Thanks again for your very quick follow-up and fstab suggestion,
Jake

---

### Post by dannyboy79 on 2012-12-11
that should be it, also as an FYI, when you make changes to your fstab file you don't need to restart the entire computer for them to take effect, just issue

sudo mount -a

and that will try to mount all the lines within the fstab file. Also, to clarify, you keep mentioning "root" access, it's not that you have root access, it was just prior you didn't have the correct permissions on the efile folder so unless you escalated your privileges to root, you couldn't write to it. Issue ls -la /mnt/ now and see who owns the folder? It should be "root" anymore.

 Glad you got it sorted! You can mark it solved.

---

### Post by jakfish on 2012-12-11
Yes, that's exactly it:

jake@S10-3t:~$ ls -la /mnt/
total 8
drwxr-xr-x  3 root root 4096 Nov 28 13:50 .
drwxr-xr-x 23 root root 4096 Dec  7 08:55 ..
drwxrwxrwx  1 jake jake    0 Dec 11  2012 efile

Again, much obliged for your assistance,
Jake

---

