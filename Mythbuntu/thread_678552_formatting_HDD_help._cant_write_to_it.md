---
title: "formatting HDD help. cant write to it"
date: 2008-01-26
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-01-26
so i have my new MythTV backend box togehter and everything is running quite well. 

now i have 3x500 GB HDDs for video storage (full ISO dvd rips w/ menus). now initially i had just the 1 HDD but that filled up rather quick. so i got 2 more, installed them, yet ubuntu could not see them. i figured it was because they werent formatted yet, so i formatted them both to XFS using GParted (which took all of about 10 seconds, is that normal? i thought HDDs of this size took hours to format?) then i restarted the computer and upon login, i can see the drives now. so i attempted to copy all my current DVD rips from the first drive to one of the new ones but it wont let me. the permissions are set as 

user: root, read and write
others: read only

so i tried to chmod to change the permissions

```
sudo chmod -R 777 /dev/sdb1
``` 

but no permissions were changed? did i do that correctly? 

these three drives will be used for video storage only. they wont have an OS installed on them or anything. how would i set each of these drives to be the place to hold the movies? just set the directory to "/dev/sda1, /dev/sdb1, /dev/sdc1" 

any help with this would be appreciated.

---

### Post by gsrcrxsi on 2008-01-26
well i figured it out. i needed to mount the drive then do chmod for /media/disk. 

which brings me to another question. ubuntu sees the drives just as "500 GB volume" when i mount it, it makes it just "disk", "disk-1" and so on, in the order that i mount them. is there a way to mount them and have them be actually named something else? and have them be named the same thing every time they are mounted?

secondly, since these drives are being used seperately for video storage. i need too add them as seperate video directories. how exactly do i do that? when i go into media settings and then video settings ive tried adding 2 directories on the single line but i must be getting te syntax wrong becuse nothing seems to work. any tips?

---

### Post by ubnewbie2 on 2008-01-27
> **gsrcrxsi said:**
> well i figured it out. i needed to mount the drive then do chmod for /media/disk. 

which brings me to another question. ubuntu sees the drives just as "500 GB volume" when i mount it, it makes it just "disk", "disk-1" and so on, in the order that i mount them. is there a way to mount them and have them be actually named something else? and have them be named the same thing every time they are mounted?

secondly, since these drives are being used seperately for video storage. i need too add them as seperate video directories. how exactly do i do that? when i go into media settings and then video settings ive tried adding 2 directories on the single line but i must be getting te syntax wrong becuse nothing seems to work. any tips?

You are just seeing the names ubuntu gives them automatically.  You need to mount them yourself to a mount point that you create with the name you want.  A mount point is just a directory.

Then, to get them to mount automatically, you need to add a line to /etc/fstab

here's a line from mine that mounts my /dev/hda1 to /mnt/data as an example

/dev/hda1       /mnt/data       ext3    defaults        0       2

---

### Post by newlinux on 2008-01-27
> **ubnewbie2 said:**
> You are just seeing the names ubuntu gives them automatically.  You need to mount them yourself to a mount point that you create with the name you want.  A mount point is just a directory.

Then, to get them to mount automatically, you need to add a line to /etc/fstab

here's a line from mine that mounts my /dev/hda1 to /mnt/data as an example

/dev/hda1       /mnt/data       ext3    defaults        0       2

Just to be clear, you will want to create the mount point first (in this example mkdir /mnt/data).
```

man fstab

```
will give you more info on /etc/fstab mounting arguments.

---

### Post by gsrcrxsi on 2008-01-27
i thought mkdir just made a folder? isnt /media/disk already a mount point?

im still a little new to all the terminal commands. forgive my ignorance. im just unsure EXACTLY what i have to do at this point to do what im trying to do.

---

### Post by newlinux on 2008-01-27
It does make a folder. If you want to mount to a mount point (folder) that doesn't already exist you would need to create it first before mounting it to that location. If it already exists you can mount it to that location without creating it. So where do you want to mount it to, and what filesystem is it?

---

### Post by newlinux on 2008-01-27
Oh, and you can add two different folders to mythvideo by separating them with a colon.

---

### Post by gsrcrxsi on 2008-01-27
BLAST! the one seperation tequnique i didnt try LOL. i tried spaces, commas, and semi-colons. so do i seperate with ONLY a colon? or colon and a space? or does it not matter? where i mount it to really doesnt matter to me, i just need a it mounted to a directory that the name isnt going to change. the file system of all 3 500 GB data drives is XFS.

ok so from what it sounds like i need to do the following:

1. mkdir my mount point (/mnt/videos1, /mnt/videos2, /mnt/videos3 for example)
2. add this mounting to fstab like so
```

/dev/sda1 /mnt/videos1 xfs defaults 0 0
/dev/sdb1 /mnt/videos2 xfs defaults 0 0
/dev/sdc1 /mnt/videos3 xfs defaults 0 0

```
3. add video directories to mythtv like so
```

/mnt/videos1:/mnt/videos2:/mnt/videos3

```

do i have this?

---

### Post by ubnewbie2 on 2008-01-27
Yes, seems so, but I recommend a 2 for the last field in fstab, not 0.  This just makes sure the filesystem get's checked at boot time.

---

### Post by gsrcrxsi on 2008-01-27
horray it works!

now time to reconfigure the frontend to be able to recieve this content....

---

### Post by newlinux on 2008-01-27
I don't know if this has changed in Gutsy (my servers are edgy and feisty) but for me removable drives don't show up in the same place all the time (e.g. it will change from /dev/sdb1 to /dev/sdc1) which breaks fstab. So to fix this I mount by uuid for the drive, which doesn't change unless you reformat.

[http://ubuntuforums.org/showthread.php?t=626626](http://ubuntuforums.org/showthread.php?t=626626)
[http://ubuntuforums.org/showthread.php?t=384006](http://ubuntuforums.org/showthread.php?t=384006)

You can also change the label...

---

### Post by gsrcrxsi on 2008-01-27
how would an internal HDD be classified as removable? everything works fine for me, each drive is always the same when it boots up.

---

### Post by newlinux on 2008-01-27
Error in my reading. I thought it was an external drive... I was only half awake with a crying baby :)  Another minor point, you currently have your your three drives set to never be checked by fsck (6th argument in fstab is 0). I think it prudent to have them checked since you might use them a lot. That can be checked simultaneously as they are separate drives.

---

### Post by gsrcrxsi on 2008-01-27
yea the other guy mentioned that. so i set it to 2. what are my different options? is there a value that i can set to have it check like every week or something, not just at boot? i mean this is a server after all, once its all setup, it has the potential to run for weeks, months, and years without needing a reboot.

---

### Post by newlinux on 2008-01-27
That option doesn't change how often it is fsck'd (except that 0 means it never is). That option sets up the sequencing (all partitions with the number 1 can be checked simultaneously, all with the number 2 can be checked at the same time). You just don't want two partitions on the same drive checked at the same time. Chances are you root partition on your primary drive is set to 1. If you root partition is set to 1 and your three new drives are set to 2 then the root partition will be checked first, and when they are done the 3 new drives would be checked, if they are all scheduled to be checked at the same time). If they are all set to one they would all be checked simultaneously, which would save you some time.

```
tune2fs -c <number_of_mounts> /dev/<xxxx>
``` 
will set the number of times a filesystem is mounted before being checked at boot by fsck. Since I don't believe you can run fsck on a mounted filesystem you would need to create some type of cronjob to unmount the drive fsck it, and then remount it if you want to run it while your computer is booted. This would be tricky since your machine wouldn't have access to this drive during this time, and you don't know how long fsck will take to run.

---

### Post by gsrcrxsi on 2008-01-28
ok well i got everything sorted out almost. 

i have the backend mounting the HDDs to my video directories /mnt/videos* in /etc/fstab
```

/dev/sda1       /mnt/videos1    xfs     defaults   0     2
/dev/sdb1       /mnt/videos2    xfs     defaults   0     2
/dev/sdc1       /mnt/videos3    xfs     defaults   0     2

```

then i have the backend sharing my video driectories in /etc/exports. 
```

/var/lib/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)
/mnt/videos1   *(ro,async,no_root_squash,no_subtree_check)
/mnt/videos2   *(ro,async,no_root_squash,no_subtree_check)
/mnt/videos3   *(ro,async,no_root_squash,no_subtree_check)

```

then on the frontend i created the new video directories and have /etc/fstab so that the backend video directories get mounted at boot

```

192.168.2.105://mnt/videos1 /mnt/videos1  nfs  defaults,user,soft,nointr 0 0
192.168.2.105://mnt/videos2 /mnt/videos2  nfs  defaults,user,soft,nointr 0 0
192.168.2.105://mnt/videos3 /mnt/videos3  nfs  defaults,user,soft,nointr 0 0

```

restarted and changed mythtv's video directories, and opened up the frontend and went to see if my videos were there. HORRAY! they are there and when i select them they play. at least some of them do. some play fine, and some are all glitchy and studdery. its not the movie files themselves becuase they play fine on my backend. XvMC is not on, ive tried many different settings, but cant get anything to work. any ideas?

---

### Post by newlinux on 2008-01-28
what kind of network are you running? Which types of files don't work well (is there a pattern)? Are you using the internal player to play them? Have you tried playing them outside of mythtv with mplayer on your frontend? This can help narrow down if it is a myth problem or machine/network problem.

---

### Post by gsrcrxsi on 2008-01-28
wired network. no difference in file types, they are all ISO's. ill try to play them in the other players to narrow it down, and let you know what i find

---

### Post by gsrcrxsi on 2008-01-28
same issues in VLC and Xine

---

### Post by gsrcrxsi on 2008-01-28
proprietary codecs was my problem. lol

---

### Post by gsrcrxsi on 2008-01-30
off topic...

how does changing the video directory affect ripping DVD's? because ever since i did all this stuff of changing video directories, import/rip dvd in myth has not worked at all. when i tell it to rip, it takes me to the rip/transcode screen then says nothing left to do. mythfrontend.log had absolutely NOTHING about what was going on. just told me that the transcode gui was brought up. 

so i wiped the OS and reinstalled. it all seems to be working fine, but im a little worried that if i change the directories around again that ripping dvd's will stop working again. 

so how does changing video directories affect all this? will it write to the first one? still write to /var/lib/mythtv/videos? 

thanks

---

### Post by gsrcrxsi on 2008-01-31
well its confirmed. having multiple video directories makes dvd ripping no longer work. i assume because it doesnt know what directory to write the file to. is there any way to fix this? is there a way to have it ask you which directory you want to write to? or have it always write to a certain one?

---

