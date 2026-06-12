---
title: "What is the best way to add a hard drive to mythtv?"
date: 2011-02-19
forum: Mythbuntu
---

### Post by williammanda on 2011-02-19
I want to add a hard drive to increase the space for recordings. Do I just add the drive under storage groups for recordings? If so do I enter /media/sdb1? If not please advise.
Thanks

---

### Post by LowSky on 2011-02-19
I have 4 hard drives listed under storage groups. enter the hard drive's location is all you need to do, Personally name the folder and if possible make usre the drive will always mount the same. Personally I use UUID in fstab

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by PaulReaver on 2011-02-19
> **williammanda said:**
> I want to add a hard drive to increase the space for recordings. Do I just add the drive under storage groups for recordings? If so do I enter /media/sdb1? If not please advise.
Thanks

NO

you'll need to add it to the bottom of your fstab so that it is automatically mounted on boot..... 

you will also need to change the permissions so that the mythtv group can access it.

it should look something like this.....for a jfs formatted partition called /mythtv

# /mythtv on /dev/sdb1
UUID=<your disks UUID goes here> /mythtv         jfs     defaults        0       2


THEN you can add it to the mythtv options as /mythtv

hope it helps

---

### Post by mr_luksom on 2011-02-20
From what is written above, it sounds like I went about it the hard way for a little flexibility.

I created an LVM partition using new and old drives, and gave that directory as the only storage directory.

Wiped all previous recordings in the process (I was both ok and expecting that), however it does give me LVM's flexibility to add/remove/resize partitions and drives.

This was mostly motivated by having non-myth media on the same LVM.

---

### Post by williammanda on 2011-02-20
OK
This is what I was afraid of....There needs to be a way to add storage so that the newbee can do it. Can anyone layout a simple way to add a hard drive?

---

### Post by williammanda on 2011-02-20
> **LowSky said:**
> I have 4 hard drives listed under storage groups. enter the hard drive's location is all you need to do, Personally name the folder and if possible make usre the drive will always mount the same. Personally I use UUID in fstab

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

I added a directory /media/sdb1/recordings under storage groups but I don't see the added space or another drive. What's the simplest way to do this?

---

### Post by williammanda on 2011-02-20
> **PaulReaver said:**
> NO

you'll need to add it to the bottom of your fstab so that it is automatically mounted on boot..... 

you will also need to change the permissions so that the mythtv group can access it.

it should look something like this.....for a jfs formatted partition called /mythtv

# /mythtv on /dev/sdb1
UUID=<your disks UUID goes here> /mythtv         jfs     defaults        0       2


THEN you can add it to the mythtv options as /mythtv

hope it helps

Thanks for the help but the everyday person will puke when they see what you said to do.

---

### Post by PaulReaver on 2011-02-20
we need to add your partition sdb1 to the list of partitions ubuntu looks though in the file /etc/fstab.

---

### Post by williammanda on 2011-02-20
What everyone needs to understand is that this is something that the newbee needs to be able to do....just like installing Mythbuntu. Don't tell me like I know command line linux...explain it so that the everyday person can add a hard drive. If not this question will be here day after day.

---

### Post by PaulReaver on 2011-02-20
I know mate...... I'll walk you through it one step at a time....

right

run this in a terminal

ls -l /dev/disk/by-uuid | grep 'sdb1'


and paste the output up here

---

### Post by williammanda on 2011-02-20
william@C2Q:~$ ls -l /dev/disk/by-uuid | grep 'sdb1'
lrwxrwxrwx 1 root root 10 2011-02-20 00:06 45836205-bdee-44bc-add2-b44e04936b5b -> ../../sdb1

There is the output from your request

---

### Post by PaulReaver on 2011-02-20
right one last one can you paste the output from

fsck -N /dev/sdb1

---

### Post by williammanda on 2011-02-20
> **PaulReaver said:**
> right one last one can you paste the output from

fsck -N /dev/sdb1

william@C2Q:~$ fsck -N /dev/sdb1
fsck from util-linux-ng 2.17.2
[/sbin/fsck.ext4 (1) -- /media/sdb1] fsck.ext4 /dev/sdb1

---

### Post by PaulReaver on 2011-02-20
last bit 
open up /etc/fstab
with 
sudo /etc/fstab 

and paste this into the bottom of it and save

# /mythtv on /dev/sdb1
UUID=45836205-bdee-44bc-add2-b44e04936b5b /mythtv ext4 defaults 0 2


when you reboot your pc, sdb1 will be mounted at /mythtv

:)

all done apart from the permissions and adding it to mythtv

---

### Post by williammanda on 2011-02-20
From the replies so far...adding a hard drive is like giving birth. I have had advise to make it LVM (which I thought was redundant with storage groups) to command line entries. So to make this simple as Mythbuntu....Is there a way to add a hard drive to increase storage...whether it be for recordings, videos, etc...?

---

### Post by williammanda on 2011-02-20
> **PaulReaver said:**
> last bit 
open up /etc/fstab
with 
sudo /etc/fstab 

and paste this into the bottom of it and save

# /mythtv on /dev/sdb1
UUID=45836205-bdee-44bc-add2-b44e04936b5b /mythtv ext4 defaults 0 2


when you reboot your pc, sdb1 will be mounted at /mythtv

:)

all done apart from the permissions and adding it to mythtv

My drive is mounted and works. I need the first question answered.... I have sdb1 working....I need to get sdb1 setup to expand the recordings of the orginal drive

---

### Post by PaulReaver on 2011-02-20
it works :)   good stuff.... 

you'll need to give user group mythtv read write permissions to /mythtv

do you know how to add storage groups to mythtv?

---

### Post by williammanda on 2011-02-20
> **PaulReaver said:**
> it works :)   good stuff.... 

you'll need to give user group mythtv read write permissions to /mythtv

do you know how to add storage groups to mythtv?


That happens when you set up Mythbuntu....this isn't helping out...If I were to ask the question of "how do I added more hard drive storage"...I would be pissed at this point. Sorry but you have listened to the initial question of the post.

---

### Post by williammanda on 2011-02-20
> **PaulReaver said:**
> it works :)   good stuff.... 

you'll need to give user group mythtv read write permissions to /mythtv

do you know how to add storage groups to mythtv?

Yes I do...read the 1st post.

---

### Post by PaulReaver on 2011-02-20
Oh right so am I wasting your time???

what I was doing was trying to do was make mounting a hard disk as easy as possible (babysteps)

then was going to sort out folder permissions of /mythtv give read write permissions to mythtv group

and then tell you how to set up storage groups in mythbackend


but I didn't realize I was doing all this for my benefit... sorry to keep you




information is all here

storage groups
[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

file permissions
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


have a nice day :)

---

### Post by williammanda on 2011-02-20
It would be nice if people would read the original posts before replying....they then ask questions like you never posted any information.....several posts later....they then ask information like you never posted it.

---

### Post by williammanda on 2011-02-20
> **PaulReaver said:**
> Oh right so am I wasting your time???

what I was doing was trying to do was make mounting a hard disk as easy as possible (babysteps)

then was going to sort out folder permissions of /mythtv give read write permissions to mythtv group

and then tell you how to set up storage groups in mythbackend


but I didn't realize I was doing all this for my benefit... sorry to keep you




information is all here

storage groups
[http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

file permissions
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


have a nice day :)

I already had it mounted...that wasn't the question....please read the posts! Not only that ...please answer my post....

---

### Post by PaulReaver on 2011-02-20
all I'm going to say is that mythtv (more importantly the mysql database) does not like to find files missing.... double clicking a hard disk so that it temporarily mounts in /media is not good enough for mysql... it had to be mounted properly.

don't believe me this is how its done look [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=146060") 

mythtv folder permissions 

$ cd /
$ sudo chown <your username>:mythtv mythtv

that'll sort out your permissions...


as for storage groups in mythtv all you do create some folders for fanart trailers videos live tv etc etc etc.....and set the directories in mythbackend storage groups...


don't want people to assume you're adding a hard disk??? don't say your adding a hard disk then

> **williammanda said:**
> I want to add a hard drive to increase the space for recordings

have a nice day :)

---

