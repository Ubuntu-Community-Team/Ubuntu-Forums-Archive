---
title: "Mythbuntu Partitioning"
date: 2008-05-02
forum: Mythbuntu
---

### Post by dsbw on 2008-05-02
Hey, mythbunters:

   I was wondering why the guided MythBuntu setup doesn't encourage a split partition: A small one for OS and the remainder of the disk for data?

   Isn't that the preferred approach?

---

### Post by volkswagner on 2008-05-03
My preferred approach is a separate drive for media.  Disk activity can hurt video playback when os and media are shared on the same physical hard drive.  This is evident with HD content or multiple tuners/frontends.

---

### Post by dsbw on 2008-05-03
> **volkswagner said:**
> My preferred approach is a separate drive for media.  Disk activity can hurt video playback when os and media are shared on the same physical hard drive.  This is evident with HD content or multiple tuners/frontends.

Well, okay, so you don't think partitioning helps in a single-user combined front/back end situation?

---

### Post by volkswagner on 2008-05-04
> **dsbw said:**
> Well, okay, so you don't think partitioning helps in a single-user combined front/back end situation?


Let my clarify.  I am sort agreeing with you.  The mythbuntu guided install is very basic.  For the best performance manual partitioning is required.  I create separate /home, /data partitions on most any install.  With myth systems including installed tuners, I like to have a dedicated drive for media, mostly recordings.

The install CD has to cover a broad range of installs, master, slave, or frontend only.

---

### Post by tgm4883 on 2008-05-04
It's my fault.  I was in charge of partitioner recipes, got busy, and ultimately failed.  8.10 will have partitioner recipes (I already have them written) for both single and dual disk setups.

Sorry for the inconvenience.

---

### Post by dsbw on 2008-05-04
> **tgm4883 said:**
> It's my fault.  I was in charge of partitioner recipes, got busy, and ultimately failed.  8.10 will have partitioner recipes (I already have them written) for both single and dual disk setups.

Sorry for the inconvenience.

Oh, no problem. Was just curious.

For those of us who would like to set up partitions (OS on 1, data on the other), what would you recommend?

---

### Post by tgm4883 on 2008-05-04
> **dsbw said:**
> Oh, no problem. Was just curious.

For those of us who would like to set up partitions (OS on 1, data on the other), what would you recommend?

The OS drive doesn't need to be that large, that is actually a problem that I have been finding is small enough drives to prevent wasted space (actually, diskless should work pretty well for this)

This is what I usually configure

/  10-12 GB  formatted to EXT3
SWAP 1GB

Second Drive 1 partition XFS


On single drive systems, I usually do

/  8-10 GB formatted to EXT3
1 GB SWAP
the rest partitioned as XFS for recordings

---

### Post by LorenzoS on 2008-05-04
tgm4883, could you provide a little guidance on the best way to configure Mythbuntu to use the 2nd drive for data, recordings, etc?  I've found a few scattered posts with differing recommendations but I still can't quite get it straight.

---

### Post by dsbw on 2008-05-05
> **tgm4883 said:**
> the rest partitioned as XFS for recordings

Is that "/var"? Can't remember offhand....

---

### Post by volkswagner on 2008-05-05
The guides I have read suggest the second partition/drive to be mounted as /var.  This is how I have it as recommended.  I wish I did it as /var/lib/mythtv/recordings.  This would be just for tv.  If you wanted all media on one drive/partition you could use mount point /var/lib/mythtv.  I discovered when trying to backup my system there are a lot of other files und /var.  So to perform a system backup I would have to exclude the mythtv folder so it would not include hundreds of gigs of video to get a complete backup. 

Please someone correct me if I am wrong.  Are the files under /var necessary for an image backup of my system?

Partitioning can be complex depending on how you use your system.  My thoughts were to have the recordings on its own partition for the defrag need.  If I have a vast media of video and music, I don't think these files will me moved much.  So why not keep them on there own partition with no need to defrag?  Or certainly not defrag as often as a /recordings partition.

So the next time I create a new install my master backend will look something like this.  Please critique so I know if this is not a good Idea.

Disk 1:
/      12gig
/home   2-50gig depending on planned use and size of actual drive
/var/lib/mythtv remainder of drive
/swap  1gig

Disk 2:
/var/lib/mythtv/recordings 500gig-1TB

How did I do?

My case only holds two hard drives.  So I am not sure with the above if LVM would even benefit?

---

### Post by tgm4883 on 2008-05-05
Use the second drive for media (recording only if you have a file server).  

The default location for recordings is /var/lib/mythtv/recordings .  I myself think this is a bad location to have the recordings (/var and all subdirectories have to be formatted on an installation)  so if you ever do a clean install instead of upgrade and want to keep your recordings then you must back up your db and all of your recordings to another hard drive (and if you have a spare HD that large, why aren't you already using it for recordings ;)  ).  IMHO a better location would be in /mythtv/recordings .  During reinstalls this partition would remain untouched (provided you didn't click on format it during install).  Then just tell mythtv to use that dir for recordings, or symlink it to /var/lib/mythtv/

You can use the second drive for storage and media.  The key here is to mount the second drive as /mythtv (or /var/lib/mythtv/ if you are using the defaults) then subdirectories of that mount would be videos, music, recordings, etc.  

dsbw:  /var/lib/mythtv if you want to follow the guide.  I prefer /mythtv/  If you have multiple drives or backends and want to use a network of storage it helps to mount your drives in such a way to be able to easily distinguish what and where they are.  The way I do it is /mythtv/hostnamedrivesize/  (i.e. /mythtv/ovit500).  Ovit is my backend, 500GB is the drive size.  So in this case, I would mount the second drive (or rest of first drive) as /mythtv/ovit500  .  Then I could easily add another drive and mount it in /mythtv/ovit1000, or mount an NFS share as /mythtv/ares300

volkswagner:  With the addition of storage groups i'm not sure you would need/want LVM.  Also, if it is a mythtv only system I don't think you would need a separate /home partition either.  In that instance, if the first drive was large enough I would create a recordings directory on their also and use storage groups.

---

### Post by johnnybirdman on 2008-05-13
I have all the OS on one 40GB HD and then on another 320GB HD all the media.  I just symlink the files on the large drive (music, video) to the folders in /mythtv/...  I just have the media drive mount in media or home (I've tried both and they seem to work)
Is there any reason this setup would be bad?  It's a new setup and I'm a first time mythbuntu user.  Any suggestions??
J.

---

### Post by poke4christ on 2008-05-13
I bought dual 320 Gig drives for my new mythbox.  How would you guys recomend me formating these?  Also, is there a detailed guide for manual partitioning?  I haven't been able to find one.

---

### Post by misterspider on 2008-06-03
I've tried editing the fstab so that a second drive mounts on bootup at /var/lib/mythtv (but i think i will change that to /mythtv/Samsung500) but i am not sure what options to use. 

/dev/sdb1  /mythtv/Samsung500    jfs    Whats_best_here?        0       2 

Thanks.

---

### Post by Titus A Duxass on 2008-06-04
This is quite an interesting thread.

Many moons ago as a Windows user I used to have two HDDs, one at 5gb for the OS and whatever I had lying around for the data files.

With linux I tried putting / on the 5gb and /home on the other which worked nicely.

Now that 5gb, or even 10gb, HDDs are becoming rare as hens' teeth I am thinking of the following:

An IDE to Compact Flash Converter - approx. 20 euros.
An 8gb Compact Flash Card - approx. 30 euros.

This would hold the / system and a large capacity SATA HDD(0.75Tb - 1.0Tb) for the other partitions.

I would like to go down to a 4gb card for even lower cost, but I think that 4gb may be too small for the / system.

Has anyone any thoughts about this set-up and the partitioning of such a set-up?

---

### Post by dsbw on 2008-06-21
Yes, others have thought of this. :)

Dunno if anyone's been successful yet.

---

### Post by Dewey_Oxberger on 2008-06-22
I'm a relative Linux/Mythtv noob but I've been doing:

A single drive with:
  10G Ext3 mounted as /
  1G swap
  The rest JFS and mounted as /htpc

Then under htpc I make:

/htpc/video
/htpc/video/livetv
/htpc/video/recordings
/htpc/video/library
/htpc/music
/htpc/pictures

And then wire up mythtv to use those directories in place of the /var/lib/mythtv directories.

Seems to work fine.

---

### Post by ChronicD on 2008-11-06
Hello 

I was wondering if anyone had any further information on a set up such as this - perhaps a different thread following it?

thanks
D

> **Titus A Duxass said:**
> This is quite an interesting thread.

Many moons ago as a Windows user I used to have two HDDs, one at 5gb for the OS and whatever I had lying around for the data files.

With linux I tried putting / on the 5gb and /home on the other which worked nicely.

Now that 5gb, or even 10gb, HDDs are becoming rare as hens' teeth I am thinking of the following:

An IDE to Compact Flash Converter - approx. 20 euros.
An 8gb Compact Flash Card - approx. 30 euros.

This would hold the / system and a large capacity SATA HDD(0.75Tb - 1.0Tb) for the other partitions.

I would like to go down to a 4gb card for even lower cost, but I think that 4gb may be too small for the / system.

Has anyone any thoughts about this set-up and the partitioning of such a set-up?

---

### Post by whosmatt on 2008-11-06
ugh i hate it when i post before looking at how old the thread is

---

### Post by yojimba on 2008-12-01
Appreciate this thread . . . 

I've managed to create a partition for media and recordings:

htpc/video
htpc/video/recordings
htpc/video/livetv
htpc/video/library
htpc/music
htpc/photos
htpc/databackup

Having a rough time figuring out exactly how to 'set permissions' so Mythtv can read and write to the above. Would someone mind spelling it out?

---

### Post by fatmonk on 2008-12-01
> **yojimba said:**
> Appreciate this thread . . . 

I've managed to create a partition for media and recordings:

htpc/video
htpc/video/recordings
htpc/video/livetv
htpc/video/library
htpc/music
htpc/photos
htpc/databackup

Having a rough time figuring out exactly how to 'set permissions' so Mythtv can read and write to the above. Would someone mind spelling it out?

Take a look at the permissions that the default directories have in /var/lib/mythtv with ls -l

If I recall correctly they are mainly drwxr-xr-x with a couple of them set with the s value.

For permissing setting details see the chmod man page (also available online at: [http://www.manpagez.com/man/1/chmod/]("http://www.manpagez.com/man/1/chmod/"))

You can them either define the directories within your myth setup or just link the old directories to the new with symbolic links (that's the easier option, I would say).

If you could paste the output of ls -l /var/lib/mythtv then I could spell out the commands to change the permissions of each for you, and give you the commands to set up the symbolic links.

-FM

---

### Post by ian dobson on 2008-12-01
> **Titus A Duxass said:**
> This is quite an interesting thread.

I am thinking of the following:

An IDE to Compact Flash Converter - approx. 20 euros.
An 8gb Compact Flash Card - approx. 30 euros.

This would hold the / system and a large capacity SATA HDD(0.75Tb - 1.0Tb) for the other partitions.

I would like to go down to a 4gb card for even lower cost, but I think that 4gb may be too small for the / system.

Has anyone any thoughts about this set-up and the partitioning of such a set-up?

I'm almost doing this. My frontend boots from a 8Gb x300 CF card in a CF-SATA adapter. As I have 1Gb ram I disabled swap and my recordings are on my backend server. I mainly did this to reduce noise (I only have one 12cm fan that runs at 100-200rpm and is silent).

I used a 2Gb IDE Flash card for about 6months in my frontend before this and had no problems.

Regards
Ian Dobson

---

### Post by yojimba on 2008-12-02
> **fatmonk said:**
> Take a look at the permissions that the default directories have in /var/lib/mythtv with ls -l

If I recall correctly they are mainly drwxr-xr-x with a couple of them set with the s value.

For permissing setting details see the chmod man page (also available online at: [http://www.manpagez.com/man/1/chmod/]("http://www.manpagez.com/man/1/chmod/"))

You can them either define the directories within your myth setup or just link the old directories to the new with symbolic links (that's the easier option, I would say).

If you could paste the output of ls -l /var/lib/mythtv then I could spell out the commands to change the permissions of each for you, and give you the commands to set up the symbolic links.

-FM

Thanks fatmonk. Below is the output of ls -l /var/lib/mythtv:

drwxrwsr-x 2 mythtv mythtv 4096 2008-10-15 23:58 music
drwxrwxr-x 2 mythtv mythtv 4096 2008-10-15 23:58 pictures
drwxrwsr-x 2 mythtv mythtv 4096 2008-10-15 23:42 recordings
drwxrwxr-x 2 mythtv mythtv 4096 2008-10-15 23:58 videos

---

### Post by fatmonk on 2008-12-02
> **yojimba said:**
> Thanks fatmonk. Below is the output of ls -l /var/lib/mythtv:

drwxrwsr-x 2 mythtv mythtv 4096 2008-10-15 23:58 music
drwxrwxr-x 2 mythtv mythtv 4096 2008-10-15 23:58 pictures
drwxrwsr-x 2 mythtv mythtv 4096 2008-10-15 23:42 recordings
drwxrwxr-x 2 mythtv mythtv 4096 2008-10-15 23:58 videos

OK, here goes then.

Assuming the following mapping:

[INDENT]/var/lib/mythtv/music -> htpc/music
/var/lib/mythtv/pictures -> htpc/photos
/var/lib/mythtv/recordings -> htpc/video/recordings
/var/lib/mythtv/videos -> htpc/video/library[/INDENT]

I'm not sure where LiveTV recordings are saved to be honest, but from the info below you should be able to suss out what's going on if you find the current LiveTV directory.

Likewise with the databackup directory.

So, step-by-step:

[LIST=1]

[*]As the partitions are created and mounted where you want them, the first thing to do is **change the permissions** on the mount point directories as follows:

```
sudo chmod a+rwx /htpc/music 
sudo chmod o-w /htpc/music 
sudo chmod g+s /htpc/music 
sudo chmod a+rwx /htpc/photos
sudo chmod o-w /htpc/photos
sudo chmod a+rwx /htpc/video/recordings
sudo chmod o-w /htpc/video/recordings
sudo chmod g+s /htpc/video/recordings
sudo chmod a+rwx /htpc/video/library
sudo chmod o-w /htpc/video/library
```

A quick explanation of the above:
[INDENT] a+rwx adds read, write and execute permissions for all users.
 o-w removes write permission for 'other' users.
 g+s adds SUID permission to the 'group' permissions.[/INDENT]
Note that there are numerical equivalents to set file and directory permissions but by using the above you can see what we are trying to acheive a bit clearer. Try an ls -l {directory} after any of those commands and you'll see the changes made.

That should be the permissions on the new partitions set up correctly...


[*]... but we should also make sure that the **user and group ownership** of the directories is correct so that the permissions apply to the correct users.

```
sudo chown mythtv:mythtv /htpc/music 
sudo chown mythtv:mythtv /htpc/photos
sudo chown mythtv:mythtv /htpc/video/recordings
sudo chown mythtv:mythtv /htpc/video/library
```

Again, by way of explanation, mythtv:mthtv is the user and group that was shown in the ls -l of /var/lib/mythtv, third and fourth columns.


[*]Next we **copy any content from the 'old' directories to the new partitions**. If you don't have any content on the box yet you can skip this bit.

```
sudo cp -rvP /var/lib/mythtv/music/* /htpc/music/.
sudo cp -rvP /var/lib/mythtv/pictures/* /htpc/photos/.
sudo cp -rvP /var/lib/mythtv/recordings/* /htpc/video/recordings/.
sudo cp -rvP /var/lib/mythtv/videos/* /htpc/video/library/.
```

Just so you know what's happening here, we're copying recursively [-r] (ie drilling down into any directories under each source directory) except for symbolic links [-P] and printing verbose output of what gets copied [-v].

You can then check that your content has copied over to the new location OK.


[*]Once you are happy that the content has copied over, we'll **rename the 'old' directories** so that we can create the symbolic links:

```
sudo mv /var/lib/mythtv/music /var/lib/mythtv/music_old
sudo mv /var/lib/mythtv/pictures /var/lib/mythtv/pictures_old
sudo mv /var/lib/mythtv/recordings /var/lib/mythtv/recordings_old
sudo mv /var/lib/mythtv/videos /var/lib/mythtv/videos_old
```


[*]Then **create the symbolic links** to the new partition mount points so that Myth can find everything:

```
sudo ln -s /htpc/music /var/lib/mythtv/music
sudo ln -s /htpc/photos /var/lib/mythtv/pictures
sudo ln -s /htpc/video/recordings /var/lib/mythtv/recordings
sudo ln -s /htpc/video/library /var/lib/mythtv/videos
```

[/LIST]

At this point everything should be in place and working.

MythTV should be able to find your music, photos, videos and recordings on the new partitions.

If everything works OK at this point and you are satisfied that your content has all been moved over to the new location, you can delete the old copy of the content in /var/lib/mythtv/*_old. I won't provide the commands to do that here as they are destructive commands that will remove content that you already have and I don't want to be responsible for someone deleting a whole library of stuff , but I'm sure you can do that bit anyway. Message boards aren't really the place for destructive commands anyway.

That should be you good to go.

It's a long winded process this way, but I've done it that way to make things as safe as possible to minimise risking losing anything.

-FM

---

### Post by yojimba on 2008-12-04
Fatmonk! Thank you very much for your help. Worked like a charm and I was able to set permissions for both LiveTV and the databackup. Greatly appreciate your help! :popcorn:

---

### Post by gator on 2008-12-04
I'm installing Mythbuntu on a pre built media center. This system will have a single 1TB drive. I'm looking at the following partions.
5GB ext3 mounted as /
3GB swap
remaining drive LVM XFS mounted as /Mythtv

i will set directorys below /Mythtv like yojimba said
The LVM will be easy to add additional drives/partitions later
a simple chmod 777 /Mythtv will work on this single user system .
A note about JFS, Mythbuntu does not seem to auto fsck if you have mount problems ( after a power failure ), you need to fsck.jfs yourself or write a small script that runs at startup to check if the directorys below /Mythtv are there.. if there not run fsck.jfs and remount. Does anyone know if XFS is the same? ;)
update 1..
It seems i only need to edit fstab and make sure the last number is not a 0 for the Mythtv partition, see here [http://chris-linux.blogspot.com/2007/02/mounting-devices.html](http://chris-linux.blogspot.com/2007/02/mounting-devices.html)
update 2...
maybe that wont work... great link.. [http://www.mythtv.org/wiki/index.php/XFS_Filesystem](http://www.mythtv.org/wiki/index.php/XFS_Filesystem)
update 3...
scrapping lvm and using storage groups!!

---

### Post by SentientFluid on 2009-01-01
I've been using Ubuntu since Hoary but this is my first time delving into Mythbuntu.  It'll be a single front/backend system (with a PVR-350) that I'll also be using as a desktop (surfing and email).

I'm curious what you'd recommend for partitioning. The system will have a 60GB, a 250GB and a 320GB for now.  This is what I was thinking:

```
On the 60GB:
/                   12gb    ext3
/home               15gb    ext3
/swap               2gb
/mythtv/recordings  30gb    xfs
```

```
On the 250GB:
/mythtv             250gb   xfs
    .../music
    .../pictures
```


```
On the 320GB:
/mythtv/video       320gb    xfs
    .../.../livetv
    .../.../library
```

Will this work?

---

### Post by Billsputters on 2009-04-10
I've done as Fat Monk suggested expect I have another level in the system.

I have /media/htpc/mythtv/video/recordings etc.

I have set the ownership, permissions and links as described.

However, as a test I imported an album of MP3's to check where it stored them. I was expecting /media/htpc/mythtv/music but instead they were placed in the usual /var/lib/music. In that directory is also the link to the /media/htpc partition. 

I'm stumped

---

### Post by Yiftos on 2009-10-16
Did you rename the original /var/lib/music before creating the link?

---

### Post by Yiftos on 2009-10-16
I have seen all the configurations of different partitions including XFS formats across different drives. However, I have yet to see anyone setup a RAID0 using XFS. Has anyone done that with success? If so, what kind of performance were you getting?

---

