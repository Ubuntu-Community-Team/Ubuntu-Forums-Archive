---
title: "Automatic mount of NAS folder fails in 10.04"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by StewD on 2010-05-09
Hi,

I'm trying to mount a folder from my NAS drive so that it always exists under /media/music.

In Ubuntu 9.10 (different machine) I did this with the following entry in /etc/fstab:

```
//servername/music /media/music smbfs username=uname,password=pword
```

I've added this to the new machine running Ubuntu 10.04. And then activate the changes with the following result: 

```
user@machinename:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on //simslink/linkmusic,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I've also had a go with the following:

```
sudo mount -t smbfs //servername/music /media/music -o username=uname password=pword
```

which fails with the following:

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

I can go through Places, Network, Double Click on the NAS, and then right click on the folder to select Mount successfully. So I know it is possible to mount the folder. But then I have to do that on every reboot...


Can anyone point me in the right direction?

Thanks,

Stew

---

### Post by StewD on 2010-05-10
Solved. I've put my solution below in case (a) others need it, (b) I need it in the future....!

To be able to mount NAS directories automatically:

Firstly, with thanks to another [post]("http://ubuntuforums.org/showthread.php?t=1474889") install necessary SAMBA software:

```
sudo apt-get install samba samba-common smbfs smbclient
```

Secondly, create directories to mount to. e.g.

```
sudo mkdir /media/music
sudo mkdir /media/videos
```

Then in /etc/fstab add lines such as:

```
//servername/yourmusic /media/music smbfs username=uername,password=password
//servername/yourvideos /media/videos smbfs username=username,password=password
```

And to activate the changes in /etc/fstab without rebooting:
```
sudo mount -a
```

Now to see whether I can get RhythmBox working....

Cheers...

S.

---

### Post by fig_wright on 2010-05-16
Thanks for the fix! :)

But this is absolutely bonkers! :mad:

Samba is a crucial application, and it takes up almost no room. Why on earth wouldnt it be installed by default!

---

### Post by RustyWyatt on 2010-05-25
Howdy,

Followed the above instructions (I'm pretty new to the command line).

When I run "sudo mount -a"

I get: "mount error(12): Cannot allocate memory"

I am running the latest updated 10.04, 32 bit on Intel hardware with 2 gigs.

All help and comments Greatly appreciated!

Thanks,
Tom

---

