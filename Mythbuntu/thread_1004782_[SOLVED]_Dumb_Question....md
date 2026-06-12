---
title: "[SOLVED] Dumb Question..."
date: 2008-12-07
forum: Mythbuntu
---

### Post by ukulele_ninja on 2008-12-07
If all of my media files are located on two external HDD's, one named 500GIG and the other named 80GIG, what is the extension path I tell mythtv to look under to find them?

---

### Post by uMuppet on 2008-12-07
Wherever your fstab has them being mounted to,
probably /media/80gig 

If you don't have them being auto-mounted it will pay to do so.  Have a search on how to auto mount external drive in your fstab file

---

### Post by ukulele_ninja on 2008-12-07
Will do, thanks for the help

If the drives are plugged in when I boot dont they auto mount?

---

### Post by majoridiot on 2008-12-07
> **ukulele_ninja said:**
> Will do, thanks for the help

If the drives are plugged in when I boot dont they auto mount?

not necessarily.

you can see what drives are mounted on boot and where they mount to by:

```
$ cat /etc/fstab
```

the first column is the drive by device (/dev) or by its UUID, the next column is the mount point.

for example, this is the fstab for this computer:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	defaults	0	0
# /dev/sda1
UUID=6c814527-5db0-4129-b3bc-f41a16213147	/	ext3	relatime,errors=remount-ro	0	1	# /dev/sda1
# /dev/sda3
UUID=5aea32d9-f557-461a-958a-011fe718ac27	/home	ext3	relatime	0	2	# /dev/sda3
# /dev/sda2
UUID=3d13dcef-1b8c-41d9-bada-a585b4022a2d	none	swap	sw	0	0	# /dev/sda2
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
```

4 devices or partitions are mounted:

/dev/sda1 is mounted to root
/dev/sda2 is swap
/dev/sda3 is /home
/dev/scd0 is mounted to /media/cdrom

as you can see, partitions sda1-3 are mounted by UUID and not the /dev location.  this is a very handy 
way to mount external drives too, as this gets around any need for udev rules, etc.

you can list all of your available drives by:

```
$ sudo fdisk -l
```

note these are *available* and not necessarily mounted.

you can get your drive UUIDs by:

```
$ ls /dev/disk/by-uuid
```

you can find a lot more info on setting up your fstab by searching the main ubunutu forums.

---

### Post by ukulele_ninja on 2008-12-08
> **uMuppet said:**
> Wherever your fstab has them being mounted to,
probably /media/80gig 

If you don't have them being auto-mounted it will pay to do so.  Have a search on how to auto mount external drive in your fstab file

I tried this, but no luck.

In the Media Setup section I have two directories that look like this"

/var/lib/mythtv/videos/:/media/500GIG/Movies

I experimenting putting an ISO file into the mythtv videos folder and it started correctly, but my external drive is still not displaying correctly.

majoridiot, 

I ran the command you suggested and got this:

root@ryan-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1a052123-b86a-418e-8546-a6658ec08cf7 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=0dc5870a-8e1a-4bfa-a841-7611da0589f3 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=03c8069d-ee35-48c3-914f-46be7afdc2f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I dont see my external HDD which sudo fdisk -l told me was sdb1. I take it this means the drive is unmounted? 

Looks like Im off to learn how to mount a drive! Thanks for everyones help!:guitar:

---

### Post by majoridiot on 2008-12-08
> **ukulele_ninja said:**
> I ran the command you suggested and got this:

root@ryan-desktop:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1a052123-b86a-418e-8546-a6658ec08cf7 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=0dc5870a-8e1a-4bfa-a841-7611da0589f3 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=03c8069d-ee35-48c3-914f-46be7afdc2f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I dont see my external HDD which sudo fdisk -l told me was sda2. I take it this means the drive is unmounted? 


exactly... it is not mounted.  once you mount it, you put the mount point in mythtv setup as you know to do
and yer good to go.

to mount it initially:

```
sudo mousepad /etc/fstab
```

then make a new entry for your external drive... this one assumes an xfs filesystem:

```
/dev/sda2 /media/EXT_HD xfs defaults 0 2
```

you will need to create the mount point you choose (in this case /media/EXT_HD) and give it write permissions:

```
$ sudo mkdir /media/EXT_HD
$ sudo chmod 777 /media/EXT_HD
```

on reboot, /dev/sda2 would be mounted to /media/EXT_HD and have read, write and execute permissions
for all users (not secure, but it's a mythbox... adjust as you need).

i definitely recommend mounting by UUID instead of the /dev location, as the latter may change
on reboot for external drives.

---

### Post by ukulele_ninja on 2008-12-08
Im sorry I edited that last post as you must have been typing, the drive is actually sdb1 and is NTFS file system, can I swap those for the commands you gave me alright?

---

### Post by ukulele_ninja on 2008-12-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1a052123-b86a-418e-8546-a6658ec08cf7 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=0dc5870a-8e1a-4bfa-a841-7611da0589f3 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=03c8069d-ee35-48c3-914f-46be7afdc2f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

this is the contents of my fstab, is it safe to add the following to a new line:

#/dev/sdb1 /media/EXT_HD NTFS defaults 0 2

---

### Post by majoridiot on 2008-12-08
> **ukulele_ninja said:**
> The file extension is NTFS, is that going to affect anything? Should I back up the drive and reformat it with Gparted?

if there is no data there you need, then yes- i would definitely reformat it to xfs or another linux
file system.

if you want to mount it just to see if it works, an appropriate fstab entry would be something like:

```
 /dev/sda2 /media/EXT_HD  ntfs defaults
```

which should be enough to get you going for testing.

---

### Post by majoridiot on 2008-12-08
> **ukulele_ninja said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1a052123-b86a-418e-8546-a6658ec08cf7 /               ext3    errors=remount-ro 0       1
# /dev/sda6
UUID=0dc5870a-8e1a-4bfa-a841-7611da0589f3 /var/lib        xfs     defaults        0       2
# /dev/sda5
UUID=03c8069d-ee35-48c3-914f-46be7afdc2f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

this is the contents of my fstab, is it safe to add the following to a new line:

#/dev/sdb1 /media/EXT_HD NTFS defaults 0 2

no # before, lowercase ntfs and make sure /media/EXT_HD exists, etc.  should have access to it on reboot.

```
/dev/sdb1 /media/EXT_HD ntfs defaults
```

---

### Post by ukulele_ninja on 2008-12-08
I dont mean to keep bugging you but im new to all this, how do I check if /media/EXT_HD exists? I think I might back all of my ISO's on this drive up and reformat it, but its worth trying.

---

### Post by majoridiot on 2008-12-08
> **ukulele_ninja said:**
> I dont mean to keep bugging you but im new to all this, how do I check if /media/EXT_HD exists? I think I might back all of my ISO's on this drive up and reformat it, but its worth trying.

from a terminal:

```
$ ls /media
```

will show you all of the directories under media.  chances are EXT_HD is not going to exist, as that
was an example i was using.

to make that directory:

```
$ sudo mkdir /media/EXT_HD
```

then open all the permissions up:

```
$ sudo chmod 777 /media/EXT_HD
```

you can substitute whatever name for EXT_HD you would like... but it *must* match the /media/... mount point you specify in fstab.

e.g. /media/500GB or /media/USB_HD, etc.

---

### Post by ukulele_ninja on 2008-12-08
> **majoridiot said:**
> from a terminal:

```
$ ls /media
```

will show you all of the directories under media.  chances are EXT_HD is not going to exist, as that
was an example i was using.

to make that directory:

```
$ sudo mkdir /media/EXT_HD
```

then open all the permissions up:

```
$ sudo chmod 777 /media/EXT_HD
```

you can substitute whatever name for EXT_HD you would like... but it *must* match the /media/... mount point you specify in fstab.

e.g. /media/500GB or /media/USB_HD, etc.

heres what I got:

ryan@ryan-desktop:~$ ls /media
500GIG  cdrom  cdrom0  cdrom1
ryan@ryan-desktop:~$

---

### Post by majoridiot on 2008-12-08
> **ukulele_ninja said:**
> heres what I got:

ryan@ryan-desktop:~$ ls /media
500GIG  cdrom  cdrom0  cdrom1
ryan@ryan-desktop:~$

if you want to use that mount point, then add this to your fstab:

```
/dev/sdb1 /media/500GIG ntfs defaults
```

then do:

```
$ sudo chmod 777 /media/500GIG
```

after rebooting, you should be able to browse the contents of that drive by looking at /media/500GIG.
all of the files and directories on that drive should be visible there.

---

### Post by ukulele_ninja on 2008-12-08
> **majoridiot said:**
> if you want to use that mount point, then add this to your fstab:

```
/dev/sdb1 /media/500GIG ntfs defaults
```

then do:

```
$ sudo chmod 777 /media/500GIG
```

after rebooting, you should be able to browse the contents of that drive by looking at /media/500GIG.
all of the files and directories on that drive should be visible there.

Tried that but the contents of my /media/500GIG/Movies folder still does not show up in mythTV. Im currently copying all my ISO files over to the main HDD and am going to reformat my Externals. What file system is best to use? I am going to be sticking with Linux for a while, but have future plans to put windows back on so what format plays well with both Os's?

---

### Post by majoridiot on 2008-12-08
> **ukulele_ninja said:**
> Tried that but the contents of my /media/500GIG/Movies folder still does not show up in mythTV. Im currently copying all my ISO files over to the main HDD and am going to reformat my Externals. What file system is best to use? I am going to be sticking with Linux for a while, but have future plans to put windows back on so what format plays well with both Os's?

if you open thunar (or another file manager) do the drive and contents show up if you browse 
/media/500GIG?

if not, then there is a problem with fstab and it should not be hard to fix.

if so, then all you need to do is add /media/500GIG/Movies to mythvideo setup path (colon separated 
with no spaces if there is something else there).  once you add it, go back into video manager, 
let it scan and you should see them.

in my experience, xfs is best linux-wise for large media files.

if you want to have read/write access from windows, ntfs is the only thing i know will work 
well enough... you might look elsewhere to see if you can get an ext2/3 windoze driver going.  
i have played with this in the past, with mixed results.

---

### Post by ukulele_ninja on 2008-12-08
I can open the drive without problem and show up fine in file manager. I have the correct path listed in the file directory but it still doesnt show up when i browse my video files. How long should it take the files to display? Maybe im being impatient?

---

### Post by majoridiot on 2008-12-08
> **ukulele_ninja said:**
> I can open the drive without problem and show up fine in file manager. I have the correct path listed in the file directory but it still doesnt show up when i browse my video files. How long should it take the files to display? Maybe im being impatient?

did you go into video manager after setting up the mount and directory correctly?  you must do this every
time you add new videos- when enter video manager, it scans the directories and adds them to the 
database.

if you already did this, then double-check your path to the videos to be sure it is correct.

---

### Post by ukulele_ninja on 2008-12-08
> **majoridiot said:**
> did you go into video manager after setting up the mount and directory correctly?  you must do this every
time you add new videos- when enter video manager, it scans the directories and adds them to the 
database.

if you already did this, then double-check your path to the videos to be sure it is correct.

No, I didnt know I had to go to video manager!

Im going to kick myself if thats all I had to do...

---

### Post by majoridiot on 2008-12-11
just to bring this thread to a close... ukulele_ninja PM'd me with continued problems.  the explanation
i sent him got him going in the right direction and he is up and running, so i am posting that reply here so
that others might possibly benefit:

<-- snipped conversation -->

you have discovered why i strongly recommended you mount by UUID instead of /dev locations- because drives 
can jump around on reboot or restart, depending on the order the system finds them.  this is not always 
consistent, as you have found.

this is the easiest way i know to accomplish what you are after:

what you want to do is determine the UUID of each drive, and mount with that.  to do this, first determine 
where each drive is currently located with sudo fdisk -l (like you have done thus far).  write down those 
locations.

once you know where each drive's /dev location is, you can now determine the drive's UUID by:

```
$ ls -l /dev/disk/by-uuid
```

this will show the UUID of each drive and where it is *currently* located... which can change as you 
have found.

you then substitute the UUID found here for the /dev/xxx argument in fstab.  as an example, here 
is what mine looks like:

```
idiot@mythbox:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2008-12-04 19:02 0cfacc6d-593d-45f5-9211-944c7007dc1c -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-12-04 19:02 5c4209a5-c8dc-470e-b8a7-6c2e6dbf86be -> ../../sdd1
lrwxrwxrwx 1 root root 10 2008-12-04 19:02 5e72ed1a-3b49-496c-9777-62bd193a4a23 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-12-04 19:02 97881b5d-1490-43fa-999e-a24965bc2591 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2008-12-04 19:02 cc342e6e-4ddf-4525-a5b8-5b46441e3fd6 -> ../../sde1
lrwxrwxrwx 1 root root 10 2008-12-04 19:02 da59f299-0fa8-4a37-a1fb-e701a7fec095 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-12-04 19:02 f51fe5ca-6c20-4827-927b-00e5f83d8395 -> ../../sda1
```

sdb1 is a media drive i want mounted at /media/HD2

sdc1 is a media drive i want mounted at /media/HD1

sdd1 is a media drive i want mounted at /media/SD

sde1 is a media drive i want mounted at /media/RECORDINGS

since i now now where each drive is, where i want it and the UUID, i can change fstab to use the UUIDs... 
which i have done.  it looks like this:

```
idiot@mythbox:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f51fe5ca-6c20-4827-927b-00e5f83d8395 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=5e72ed1a-3b49-496c-9777-62bd193a4a23 /home           ext3    relatime        0       2
# /dev/sdb2
UUID=0cfacc6d-593d-45f5-9211-944c7007dc1c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=cc342e6e-4ddf-4525-a5b8-5b46441e3fd6	/media/RECORDINGS	xfs	defaults	0	0
UUID=da59f299-0fa8-4a37-a1fb-e701a7fec095	/media/HD2	xfs	defaults	0	0
UUID=97881b5d-1490-43fa-999e-a24965bc2591	/media/HD1	xfs	defaults	0	0
UUID=5c4209a5-c8dc-470e-b8a7-6c2e6dbf86be	/media/SD	xfs	defaults	0	0
```

as you can see, all of my media drives (the last 4 entries) mount the drive by UUID to the location in /media 
i created.

now the drives can jump wherever the system might put them, but- because we are telling the system the 
UUID- it always knows what disk mounts where in /media.

a few things to remember:

you *must* either change the ownership and write permissions of *each* /media/xxx mount points so you 
can read and write to them:

```
$ sudo chown yourusername:yourusername /media/xxx
$ sudo chmod a+rwx /media/xxx
```

or, at minimum:
```
$ sudo chmod a+rwx /media/xxx
```

(note these are wide-open permissions, so adjust to your security comfort level)

also, the UUID of the drive will change with each format, so you will need to find the new UUID and adjust 
fstab if you reformat a drive.

mounting by UUID is very helpful for external drives, as they ensure a consistent mount point without 
needing udev rules... at least in my experience.

it is fine to have fstab entries for external drives, etc. that are only connected from time to time.  if 
a drive with an fstab entry is not connected on boot, the system will ignore the entry and continue on 
without issues (unless you or an app goes looking for data on that drive ;) )

---

