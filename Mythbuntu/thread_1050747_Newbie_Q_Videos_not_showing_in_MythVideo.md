---
title: "Newbie Q: Videos not showing in MythVideo"
date: 2009-01-26
forum: Mythbuntu
---

### Post by rtinker on 2009-01-26
Hi,

Tried to figure this out myself but my Linux/Myth knowledge is not that great yet.

I set up my Mythbuntu box with ext3 formatted hard drives mounted to /video/sdb, /video/sdc, etc.  The drives are good and when I used them for the default storage group for MythTV, recordings are stored there just fine. 

I went to MythVideo and set the video path to all of these locations (colon separated) e.g. /video:/video/sdb:/video/sdc...

I set up a Samba share to point to one of these directories, and copied over some videos from my Windows PC - MPG and ISO files, just as a test.

When I go to MythVideo, no files appear.  I change the browsing mode, still nothing, go to the video (media) manager and it also says there are no files.

I changed the permissions to 755 in case execution was needed, but that did not help.

Any ideas?  Thanks for the help.

---

### Post by movieman on 2009-01-26
If you manually add videos rather than recording them you need to use the Video Manager to scan for new files before they're available to play; is that the problem?

---

### Post by caminham on 2009-01-26
I have a similar setup by the sounds of it.  Most of my recordings run a User Job to encode the recordings to Xvid using nuvexport.  These go to a folder on another partition.

Before anything new shows up in these folders I have to go to Utilities/Setup->Video Manager.  It does a scan of the setup folders so after this the files are listed.

This is what Movieman is describing.

Hope it helps.

---

### Post by rtinker on 2009-01-26
Thanks for the help.

Unfortunately, one of the problems is that nothing shows up in Video Manager either.  This was the killer thing I could not figure out that led me to my post.  Without them showing up in Video Manager, I cannot enable them to be played.

I even tried setting the video path to a single one of the paths (partitions) where I can store videos, but no happiness...

Note - I can see the files in Ubuntu and can even play them using VLC, so it's not like the file encoding is wrong.  For some reason Myth just does not want to show them.

---

### Post by newlinux on 2009-01-26
Is this a combined frontend/backend?

Show us your frontend logs from when you run video manager. That might give us a better idea of what is going wrong...

---

### Post by rtinker on 2009-01-26
Here you go - I tried to mitigate the extraneous information where best I could...


```
==> /var/log/mythtv/mythfrontend.log <==
Starting mythfrontend.real..
2009-01-26 13:37:51.281 New DB connection, total: 2
2009-01-26 13:37:51.282 Connected to database 'mythconverg' at host: localhost
2009-01-26 13:37:51.285 mythfrontend version: 0.21.20080304-1 www.mythtv.org
2009-01-26 13:37:51.286 Enabled verbose msgs:  important general
2009-01-26 13:37:52.248 No theme dir: /home/ritin/.mythtv/themes/MythCenter
2009-01-26 13:37:52.250 Primary screen 0.
2009-01-26 13:37:52.250 Using screen 0, 1024x768 at 0,0
2009-01-26 13:37:52.251 No theme dir: /home/ritin/.mythtv/themes/MythCenter
2009-01-26 13:37:52.252 Switching to square mode (MythCenter)
2009-01-26 13:37:52.277 Using the Qt painter
2009-01-26 13:37:52.279 lirc init success using configuration file: /home/ritin/.mythtv/lircrc
2009-01-26 13:37:52.280 JoystickMenuClient Error: Joystick disabled - Failed to read /home/ritin/.mythtv/joystickmenurc
2009-01-26 13:37:53.170 Loading from: /usr/share/mythtv/themes/MythCenter/base.xml
2009-01-26 13:37:53.258 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-26 13:37:53.318 Registering Internal as a media playback plugin.
2009-01-26 13:37:53.451 MonitorRegisterExtensions(0x100, gif,jpg,png)
2009-01-26 13:37:53.498 Failed to run 'cdrecord --scanbus'
2009-01-26 13:37:53.503 Failed to run 'cdrecord --scanbus -dev=ATA'
2009-01-26 13:37:53.508 Failed to run 'cdrecord --scanbus -dev=ATAPI'
2009-01-26 13:37:53.555 MonitorRegisterExtensions(0x40, ogg,mp3,aac,flac)
2009-01-26 13:37:53.651 No theme dir: /home/ritin/.mythtv/themes/MythCenter
2009-01-26 13:38:00.838 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/video-ui.xml
2009-01-26 13:38:01.346 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-26 13:38:01.347 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-26 13:38:04.202 videolist.cpp: getVideoListMetadata: index out of bounds: 0
2009-01-26 13:38:07.136 XMLParse::LoadTheme using /usr/share/mythtv/themes/default/video-ui.xml

```


```
dolphin(9825) KFileMetaInfoPrivate::init: KUrl("file:///video/sdb/CANDLESHOE.iso")

```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  2.3G  8.3G  22% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  360K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.9M  502M   1% /dev
tmpfs                 505M     0  505M   0% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda6             268G  200M  268G   1% /var/lib
/dev/sdb1             459G  199M  435G   1% /video
/dev/sdc1             459G  199M  435G   1% /video
/dev/sdd1             459G  199M  435G   1% /video
/dev/sde1             459G  199M  435G   1% /video
/dev/sdb1             459G  4.6G  431G   2% /video/sdb
/dev/sdc1             459G  199M  435G   1% /video/sdc
/dev/sdd1             459G  199M  435G   1% /video/sdd
/dev/sde1             459G  199M  435G   1% /video/sde
```

==> uname -a <==
Linux Mythbuntu 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by newlinux on 2009-01-26
what is in your /etc/fstab? why do you have so many things mounted to the same place? That looks odd, and may be the problem. I'd try modifying you mounting scheme as a check, maybe simplify to having one thing mount to /video1 one to /video2, etc. so they aren't children of each other - just to take out some mounting variables.

---

### Post by rtinker on 2009-01-27
I have 4 hard drives dedicated to media storage, and then one smaller drive holds everything Mythbuntu.

The four drives were suppose to be mounted on /video/sdb, /video/sdc, /video/sdd, and /video/sde.  I suspect that my use of mount -a rather than restarting the system is why they all appeared to be mounted to the same place.  

I went ahead and modified fstab to just mount one of the drives (the first one that already had the videos) to /video/sdb and commented out the others.  I restarted the system, verified that the mount worked, I could see the files and even play them with Dolphin, but MythVideo still did not see any files.

I modified the MythVideo config so that instead of having all of the video paths in there it only had /video/sdb, but that still did not help.

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sde1
UUID=04a71959-cc0f-4a58-b978-96ec424172b3 /               ext3    errors=remount-ro 0       1
# /dev/sde6
UUID=d3edc2bb-f9bb-4d06-89c1-df78e60cd096 /var/lib        xfs     defaults        0       2
# /dev/sde5
UUID=b223f7d9-f246-4e9e-a88d-09ae8fc9c882 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
/dev/sdb1	/video/sdb		ext3	defaults	0	0
#	/dev/sdc1	/video/sdc		ext3	defaults	0	0
#	/dev/sdd1	/video/sdd		ext3	defaults	0	0
#	/dev/sde1	/video/sde		ext3	defaults	0	0
```

Does Myth not like the ext3 file system?  

Here are the mount points:
total 16
drwxrwxrwx 3 root root 4096 2009-01-25 22:25 sdb
drwxrwxrwx 2 root root 4096 2009-01-27 09:56 sdc
drwxrwxrwx 2 root root 4096 2009-01-27 09:56 sdd
drwxrwxrwx 2 root root 4096 2009-01-27 09:56 sde

Here is a partial listing of the contents of sdb:
```
total 4598000
-rw-r--r-- 1 ritin ritin  365210492 2009-01-25 12:00 3280_20090125114800.mpg
-rw-r--r-- 1 ritin ritin      13001 2009-01-25 12:42 3280_20090125114800.mpg.100x75.png
-rw-r--r-- 1 ritin ritin     129506 2009-01-25 12:47 3280_20090125114800.mpg.320x240.png
-rw-r--r-- 1 ritin ritin     127620 2009-01-25 12:47 3280_20090125114800.mpg.320x260.png
-rw-rw-rw- 1 ritin ritin     129506 2009-01-25 12:02 3280_20090125114800.mpg.png
-rwxr--r-- 1 ritin ritin 4277813248 2007-10-31 10:20 CANDLESHOE.iso
drwx------ 2 root  root       16384 2009-01-25 11:01 lost+found

```

Note that the mpg file at the top was created with MythTV and it can still be viewed in MythTV, but (for example) CANDLESHOE.iso and some other MPG files in the directory are not showing up in video manager at all.

---

### Post by newlinux on 2009-01-28
ext3 should not be a problem. What is the current output of 
```
df -h
``` 
Just to be certain...

Also, to be certain, this is a combined frontend/backend?

So you are putting your myth recordings and mythvideo files in teh same directories? Should work, but not sure why you would do that...


You should not mount using device names like /dev/sdb1 in fstab. These device names can change after reboots breaking your mounts. You should use UUIDs, which only change when the drive is reformatted.

I think we should eliminate variables step by step and troubleshoot this. Just put one file (the .iso would be fine) in /var/lib/mythtv/videos (the default location). Make sure this directory and the video file are readable by mythtv. Change your mythvideo path to /var/lib/mythtv/videos (only). Run mythfrontend with the verbosity turned up and look at the results:

```
mythfronted -v all -l <logfile>
``` where <logfile> is the name of the file you want to save the log in. Post the parts around scanning with video manager. 

Double check your file types for videos. Make sure .iso exists as a filetype to scan and isn't set as ignore in the frontend.

Hopefully this will reveal some more information. The error you are getting around video manager (the out of bound error) I've only seen when mounts are messed up.

---

### Post by rtinker on 2009-01-28
Thank you again for your help.  So as to not bother you, I am going to explore fixing the mounts better using some of the information you gave me.

The biggest problem is my newness to this - I am using what little I remember of my days using HPUX to try to sort through this as I have no Linux experience (yet). ;-)

I saw the mount that the OS install did using the UUID, and I wanted to do that, but I could not figure out how to obtain the UUID.  It does not appear in the partition manager, so I could not figure out how to find it, and a post elsewhere on the net used the method I am using so I did that.  I will go about fixing it.

The idea originally was to mount all 4 media drives to the same location thinking that the OS would manage putting the individual files on whatever drive it wanted - without some actual array software I suppose I was foolish to think that would just automatically work.  So what I will do is go ahead and set things up so that one drive goes to MythTV, and the other three, mounted separately, are for videos.

It is a combined front/back system - I will also check to make sure I did not screw up one of the questions during setup and inadvertantly blow the front/back connection.

I will try all of this before I post again and if I do, I will provide the listings/logs you suggested.

Thank you again for the help.

---

### Post by rtinker on 2009-01-28
Well, you'll be happy to hear (at least I was) that this is resolved.

I thought for SURE that Linux had evolved enough that it had the ability to sense that when I type /videos/sdb, that it KNOWS I meant /video/sdb.  :rolleyes:

I guess I was confused by MythTV using VideoS, yet the directory I created was Video.

Talk about your dumb-a__ stupid user tricks.   Chalk up another one to "The Newbie Files"

Thank you, thank you, thank you for giving me the ideas that led to my making this discovery!   You have helped to launch another Mythbuntu user...

---

### Post by newlinux on 2009-01-28
> **rtinker said:**
> 
I saw the mount that the OS install did using the UUID, and I wanted to do that, but I could not figure out how to obtain the UUID.  It does not appear in the partition manager, so I could not figure out how to find it, and a post elsewhere on the net used the method I am using so I did that.  I will go about fixing it.

The idea originally was to mount all 4 media drives to the same location thinking that the OS would manage putting the individual files on whatever drive it wanted - without some actual array software I suppose I was foolish to think that would just automatically work.  So what I will do is go ahead and set things up so that one drive goes to MythTV, and the other three, mounted separately, are for videos.
.

No worries. We all have no experience at some point. I'm glad you found a fix. A couple of things:

1. you can find the UUID by doing:
```
ls -l /dev/disk/by-uuid/
```
This will show disk the UUID is linked to.

2.. you can effectively do what you want (mounting all 4 drives in the same place) using LVM (Logical Volume Manager). But given that you can now use storage groups for myth recordings and you can specify multiple directories in mythvideo I recommend against it. in LVM, if one drive fails you will have difficulty recovering the data on the other drives.


Happy mythbuntuing...

---

