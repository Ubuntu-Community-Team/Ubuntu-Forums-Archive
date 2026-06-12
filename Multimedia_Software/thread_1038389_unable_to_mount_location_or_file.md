---
title: "unable to mount location or file"
date: 2009-01-12
forum: Multimedia Software
---

### Post by Valentine1147 on 2009-01-12
I am using Ubuntu 8.10 and i have been able to use my cd\dvd drive until when i tried to watch a dvd. it showed up in movie player but said i didnt have permission to access. so i went into root and changed the permission but it didnt affect it. so i changed it back. now i can use it at all. i have been searching many post and just getting no where. i can type sudo cat /dev/scd0 and it shows the title of dvd. i have also used another command but cant remember what it was but it showed two directories one was audio and the other was video. any help would be very helpfull. thanks in advance.

---

### Post by cb34 on 2009-01-12
im a newbie at this, but can you go into system/admin/users and groups and add yourself to the cdrom group or to a group that has access to the cdrom.

or in /etc/group file maybe...

or in /etc/fstab you have to setup the line for mounting your cdrom so you have access to it, i forget how to do this, but i think that's it.. gotta look around for info on how to modify the fstab file..

and keep in mind if you dont know.. the group file and fstab.. if you screw something up it's not good, so be very careful!

---

### Post by Valentine1147 on 2009-01-12
aleady was able to use cdrom. dont want to mess with /etc/fstab with out help. but thanks anyway

---

### Post by cb34 on 2009-01-12
well.. just in case this helps you in any way.. this is my cdrom line in fstab..
```

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
if you dont touch any other line that has to do with your main hard drives.. you shouldn't cause any problems.

you can comment out (#) your current cdrom line and try other setups till it works perfect.. ??

peaceout.

here's some fstab links:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
-----

edit-> last thing..hehe.. i actually think my fstab line up there will work because:

user - Permit any user to mount the filesystem. This automatically implies noexec, nosuid,nodev unless overridden

noauto - The filesystem will NOT be automatically mounted at startup, or when mount passed -a. You must explicitly mount the filesystem.

or this one from the second link up there:
```

/dev/scd0  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0

```

exec means allow to execute.

should work.
-----

where it says /dev/###
you should run
fdisk -l
find your cdrom drive and enter the appropriate drive in fstab.

---

### Post by Valentine1147 on 2009-01-12
im really new to this. sorry. can u give me step by step instuctions for this.  and do i need to be in (Root or does it matter what user i am in?)

---

### Post by cb34 on 2009-01-12
run this command and post the output here..
```

sudo fdisk -l

```

when you write a post here on the forum and want to post really long stuff,
put it in a box like i did above with fdisk -l, like this.

[noparse]```

fdisk -l

```[/noparse]
you dont have to.. just showin you somethin that helps with the formatting of text/code on the forum. :)

then open the fstab file, it is located at:
/etc/fstab
and post the contents here also. (copy/paste)

ill take a look and see what's up if i can see something obviously wrong.

and what exactly is it doing again? what's not workin right with the cdrom?

---

### Post by Valentine1147 on 2009-01-12
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea66ea66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1020     8193118+  27  Unknown
/dev/sda2   *        1021       10239    74051617+   7  HPFS/NTFS
/dev/sda3           10240       19457    74043585    7  HPFS/NTFS

```

```

jamie@ubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied

```

---

### Post by cb34 on 2009-01-12
ok fdisk doesn't show cdroms, just noticed..lol.. someone out there is laughing at me im sure.. no worries:)
run:
```

gksudo gedit /etc/fstab

```
you're using gnome right?

and copy paste it here. sorry, need root access to open the fstab file.

---

### Post by Valentine1147 on 2009-01-12
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
#/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0  /media/floppy0  auto rw,user,noauto  0 0

/dev/hdc  /media/cdrom0   udf,iso9660  user,noauto,utf8 0 0

```


yes i am

---

### Post by cb34 on 2009-01-12
put a disc in the drive and try from a terminal:
```

sudo mount -r -t iso9660 /dev/cdrom /media/cdrom

```

make sure the directory /media/cdrom exists.. if it doesn't first run:
```

sudo mkdir /media/cdrom

```

---

### Post by Valentine1147 on 2009-01-12
```

root@ubuntu:~# /media/cdrom
bash: /media/cdrom: is a directory

```


you could hearthe drive accessed but nothing happened

---

### Post by Valentine1147 on 2009-01-12
sorry it is on the desktop 
i opened it and there is a audio_ts and a video_ts

now what

---

### Post by cb34 on 2009-01-12
> i can type sudo cat /dev/scd0 and it shows the title of dvd

/dev/scd0 you say is where you can access and see you cd drive.. because in your fstab file, it is set to hdc

i think where it says /dev/hdc in fstab
you can change it to /dev/scd0 or even just /dev/cdrom

and to execute files on the cd/dvd, not just read them, you add the exec option
so in the end it should look like this:
```

/dev/scd0  /media/cdrom    udf,iso9660  ro,exec,user,noauto,utf8 0 0
or
/dev/cdrom

```
(mount the device on scd0 to /media/cdrom with read-only, execute access, allow all users to mount, and noauto mount when you boot up. unless you dont want the drive to have execute access because you have some other users using the machine or something, then dont add the exec option, your choice. but with read access you should be able to read anything on the disc, watch movies etc.)

try that.
u can unmount the cd rom drive right now, then reboot after saving the changes and see if just popping a cd in the drive gives you access.
to unmount the cdrom right now..
sudo umount /dev/cdrom
-----

p.s. from your other post.. video_ts.. in that directory is where the movie is to get at it manually.
but you should be able after everything is set up properly to just do- Load dvd from a movie player program.

---

### Post by Valentine1147 on 2009-01-12
did what u said and when i rebooted i went back into my user and it is still doing the same thing. should i mount like last time?

```

sudo mount -r -t iso9660 /dev/cdrom /media/cdrom

```



ps/ i did the mount and i came on desktop that way. i got the error: Could not open location; you might not have permission to open the file.

---

### Post by cb34 on 2009-01-12
yes, that is how to mount the drive manually.. but it should work from the fstab file.. dont get it?

what's the error you're getting.
dmesg |grep scd
or
dmesg |grep hda
dmesg |grep hdb
dmesg |grep hdc

find any error messages to do with the cd drive at boot.. i dont get it..

can u do:
```

chown yourusername:yourusername /media/cdrom

```
so you own the /media/cdrom directory.

---

### Post by cb34 on 2009-01-12
no.. wait..

do:
```

gksudo gedit /etc/group

```

look for the line that says cdrom
after the colon add your username like you see it done all over in that file, save n exit.

after a reboot, that should work without having to manually mount the drive.... i think.
or at least you'll have permission on the drive.

---

### Post by Valentine1147 on 2009-01-12
when i open the cd/dvd drive from the places/computer i get Uable to mount location: Can't mount file

---

### Post by cb34 on 2009-01-12
i think im on to something how to get it working?

are you the only user on this machine?

after you try to modify the group file, lemme know...
and you'll only know after a reboot, cuz that's when the fstab file getes loaded, i dont know how to reload the fstab file manually. well actually i do sudo mount -a ... but i dont know if that will help to test n see if the cdrom is loading up properly.

---

### Post by Valentine1147 on 2009-01-12
yes just me and root. what do u want me to do?

---

### Post by cb34 on 2009-01-12
try in the terminal:
cd ~
ls -ln
and in the 2nd and 3rd column, does it say 1000? if so use what i wrote below, otherwise, what it says in the 2nd and 3rd column, use that number.. that is you.
root is 0
first user that is created on a fresh install is assigned 1000
```

/dev/cdrom  /media/cdrom    udf,iso9660  ro,exec,uid=1000,gid=1000,noauto,utf8 0 0

```

i think instead of rebooting, you can do:
sudo umount /dev/cdrom
then
sudo mount -a (when a cd is in the drive) and check if you have access.. if it doesn't mount like this, try to mount manually like you did before and check for access.

---

### Post by cb34 on 2009-01-12
you can try to manually mount like this:
```

sudo mount -t iso9660 -o ro,exec,uid=1000,gid=1000,noauto /dev/cdrom /media/cdrom

```

---

### Post by Valentine1147 on 2009-01-12
had to mount it by 
sudo mount -r -t iso9660 /dev/cdrom /media/cdrom
 
then when it mounted on desktop i right clicked and open with movie player and it says:  Could not open location; you might not have permission to open the file.

---

### Post by cb34 on 2009-01-12
unmunt and remount with the command above..

and also.. did you modify the /etc/group file and add your username to the cdrom group?

oh man, i think i got somethin else... the cdrom dir is just a link to the cdrom0 dir in /media

u need to apply permission to the cdrom0 dir not only cdrom.. i think.. im tryin man,,:)
try if all else fails..

sudo chown username:username /media/cdrom
sudo chown username:username /media/cdrom0

(username= your user name)
-----

after this i just dont know man.. something in here has to work, some combination of things.. it's gotta.. somehow..

---

### Post by Valentine1147 on 2009-01-12
did what u said. then when i opened with movie player is gives same error
Could not open location; you might not have permission to open the file.

---

### Post by cb34 on 2009-01-12
what i wrote in post #21.. that should mount the cdrom drive with user 1000 and group 1000 permissions, which is you. if you're sure you are user 1000, hmmmm....

in /etc/group, putting your user in cdrom group..
chown'ing the media/cdrom directories with your uusername..
manually mounting giving permission to user/group 1000, which should be you if its only u and root on the machine, and still nothing.. i dont get it.. 

and the funny thing is.. i had this exact problem a while back, and i somehow fixed it from searching around this forum.. i just cant remember what exactly it was... there is a fix for this.

did u try to access some other cd/dvd because i just read this:

I get "/cdrom: Permission denied" errors

Some CDs have root directory file permissions that only allow user root to read them. This is an error on the part of the CD-ROM vendor and is a real inconvenience. A more common occurrence is for certain files or directories not to be world readable. Some people have patched their kernels to work around the problem.
-----

BING! actually i have another small idea to try.. hahahaha ..

go into /SYSTEM/ADMINISTRATION/Users and Groups
unlock it
click on your username
then properties
at the top, click on the User Privileges tab
see where it says Use CD-ROM devices ? is it checked?
you may have to reboot for this to take effect if it wasn't checked and you now check it.

and if that doesn't work, i actually have another few ideas..lol
all up to you if you're sick of this already or you want me to keep going.. :P but the next few ideas, i'm almost 100% that one of them is the cure.

there's a couple things..
but i dont wanna just throw out commands for you to run, we need to keep track of the changes and go down a checklist and repeat check a few things we already fiddled with.. so im not done with ideas yet. :D
but i think i know what to do now. the forum down gave me a minute to read some things. ;)
---

and if absolutely nothing normal works like how it should be set up..
i know for sure a work around to mount the cdrom with user permission.

---

### Post by cb34 on 2009-01-14
what i wrote in post #21.. that should mount the cdrom drive with user 1000 and group 1000 permissions, which is you. if you're sure you are user 1000, hmmmm....
(maybe you need to run it without sudo now since you have the -user- option in your fstab, which means any user can mount, so maybe when mounting with sudo, it is making the mount owned by root...???)

in /etc/group, putting your user in cdrom group..
chown'ing the media/cdrom directories with your username..
manually mounting giving permission to user/group 1000, which should be you if its only u and root on the machine, and still nothing.. i dont get it.. 

and the funny thing is.. i had this exact problem a while back, and i somehow fixed it from searching around this forum.. i just cant remember what exactly it was... there is a fix for this.

did u try to access some other cd/dvd because i just read this:

Some CDs have root directory file permissions that only allow user root to read them. This is an error on the part of the CD-ROM vendor and is a real inconvenience. A more common occurrence is for certain files or directories not to be world readable. Some people have patched their kernels to work around the problem.
-----

BING! actually i have another small idea to try.. hahahaha ..

go into /SYSTEM/ADMINISTRATION/Users and Groups
unlock it
click on your username
then properties
at the top, click on the User Privileges tab
see where it says Use CD-ROM devices ? is it checked?
you may have to reboot for this to take effect if it wasn't checked and you now check it.

and if that doesn't work, i actually have another few ideas..lol
-----

ok.. i was bored, so i wrote all this from some article i found..
so if going to Users and Groups and ticking the cdrom option, then rebooting didn't work..
---

this is how it's done: ... i think..:p

you have to mount the cdrom like you did before, then in the terminal type:
```

df

```
find what ubuntu assigned to the cd drive.. all the way on the left, /dev/###
(that /dev/### is what you have to enter in the command below and fstab.. remember this..)

then make sure you unmount the cd drive:
```

sudo umount /dev/cdrom

```

then type:
```

sudo chmod 777 /media/cdrom
sudo chmod 666 /dev/###

```
(put instead of ### the proper entry that you found for the cd drive when you ran df, something like hd#? or scd#?)

now edit the fstab file:
```

gksudo gedit /etc/fstab

and make the cdrom line look like this:

/dev/###  /media/cdrom0    udf,iso9660    ro,user,noauto,utf8    0  0

```
(enter proper device for /dev/###?, and make you sure you dont have duplicate lines for the cdrom by mistake, only 1 line per drive in fstab. commenting out any unused lines is ok.)

save,close and reboot.

then try to put a cd in the drive, or open and close if one's in there already.
using gnome-volume-manager it should pop up automatically.. but if not.. you can now mount the cd drive without root permission by just typing:
```

mount /media/cdrom

```
no need for sudu, and you should now have full permissions on the cd drive.
i hope. :D

---

