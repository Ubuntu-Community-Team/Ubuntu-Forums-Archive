---
title: "No videos in Video Manager"
date: 2009-07-21
forum: Mythbuntu
---

### Post by chipppy on 2009-07-21
Good evening

This is a bit of strange one.  I have had this problem since I did a clean install of Mythbuntu 9.04

When I go, via the mythtv front-end, into Utilities/Setup ==> Video Manager, it says there are no videos.  Also there is a black box in the middle of the, normally blue, screen that has **Enter IMBD number** in it.

this would normally mean that I had a serious problem but for some strange reason there is no real problem.  I can see all my movies if I want to play one from my collection.  If I add some more movies into the Videos folder and then go into Utilities/Setup ==> Video Manager, as I normally would, then the new videos appear in my collection and are good to play.

Strange problem.  Has anyone seen this before?
I want to fix this problem as I want to get the cVideo Cover art to come up.  At the moment I just get the picture of a folder.  As my kids are still young (1.5, 3, & 5)  They find it hard to read the titles.  It would be great to get the cover art/posters working so they can pick there own movies to watch.

Any and all help is greatly appreiciated

Cheers
chipppy

---

### Post by klc5555 on 2009-07-21
A perennial. :)

[http://ubuntuforums.org/showthread.php?t=1215356](http://ubuntuforums.org/showthread.php?t=1215356)

---

### Post by chipppy on 2009-07-21
Good Evening

Cool read through the lot and finally found a little scrpt in the actual bug report (bug #339880) 
```
find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g'
```
that fixed up the black screen with **enter IMDB number**. That part is now SOLVED 

But I still dont have anything listed in there.  It now says **No Videos found** and still all the video are there in the play list and work fine.

Any ideas for the missing files from the Video Manager?

Cheers
chipppy

---

### Post by klc5555 on 2009-07-22
> **chipppy said:**
> Good Evening

Cool read through the lot and finally found a little scrpt in the actual bug report (bug #339880) 
```
find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g'
```
that fixed up the black screen with **enter IMDB number**. That part is now SOLVED 

But I still dont have anything listed in there.  It now says **No Videos found** and still all the video are there in the play list and work fine.

Any ideas for the missing files from the Video Manager?

Cheers
chipppy

No clue, except, since this a clean installation, to check whether the video directory and perhaps file extensions are properly set in MythVideo setup (Settings-> Videos Settings-> General Settings). And that your user account has been added to the mythtv group so that your frontend has appropriate read/write access to the directories under /var/lib/mythtv

---

### Post by chipppy on 2009-07-23
Good evening

I had a look through the area that you recommended and a heap of other area and couldnt find anything that looked like the bit referencing the video manager or the like.
Do you know which specific spot I need to check?

How do I check if my user account has been added to the mythTV user group?

Cheers
chipppy

---

### Post by klc5555 on 2009-07-23
> **chipppy said:**
> Good evening

I had a look through the area that you recommended and a heap of other area and couldnt find anything that looked like the bit referencing the video manager or the like.
Do you know which specific spot I need to check?

How do I check if my user account has been added to the mythTV user group?

Cheers
chipppy

1) Relevant section from the Mythtv user manual [http://www.mythtv.org/wiki/MythVideo](http://www.mythtv.org/wiki/MythVideo)
...  
"Configuration
"Selecting Folders

**"In the MythVideo setup (Settings-> Videos Settings-> General Settings), you can enter your video directories as a colon separated list.**

"All video files must be readable as part of the local filesystem. This means if you have a separate frontends and backends, you must share the directories remotely as described in Mediashares (perhaps with NFS)."

(etc.)
........

2) Users and groups are managed from the appropriate utility ("users and groups")in the desktop's system menu. Generally, also, the first time you ran the Mythtv backend setup from the Myth control centre in the frontend, a dialogue box should have popped up offering to add your user to the "mythtv group". But this may not have happened in your case.

Simple instructions for using this "users and groups" utility in Xubuntu (that is, "Mythbuntu") are here: [http://linux.about.com/od/xubuntu_doc/a/xubudg26t01.htm](http://linux.about.com/od/xubuntu_doc/a/xubudg26t01.htm)

---

### Post by chipppy on 2009-07-24
Good Evening

i went through the setup and all looks good.  The folder for the video is selected/setup correctly.  I recently added in a new HDD and setup via volume group method and copied all the videos over to the new HDD.  All is working fine, but still no videos fualt when I go into video manager.

I checked through the users & groups and both root and chipppy are ticked for the mythtv group.  i added both into mySQL as a test and this didnt fix the problem.

I had a bit of a read around the wiki and couldnt find anything that might be something to do with the issue.  I did figure out how to manually load the posters if I can figure out how to name then right and change the metadata, but I want to fix the problem not bandaid it.

I am at a loss for what to do next.  Any ideas?

Cheers
chipppy :(     ](*,)

---

### Post by klc5555 on 2009-07-24
> **chipppy said:**
> Good Evening

i went through the setup and all looks good.  The folder for the video is selected/setup correctly.  I recently added in a new HDD and setup via volume group method and copied all the videos over to the new HDD.  All is working fine, but still no videos fualt when I go into video manager.

I checked through the users & groups and both root and chipppy are ticked for the mythtv group.  i added both into mySQL as a test and this didnt fix the problem.

I had a bit of a read around the wiki and couldnt find anything that might be something to do with the issue.  I did figure out how to manually load the posters if I can figure out how to name then right and change the metadata, but I want to fix the problem not bandaid it.

I am at a loss for what to do next.  Any ideas?

Cheers
chipppy :(     ](*,)

If you just added the HDD the videos directory is located on, the mount point for the drive (that is, wherever you have it mounted in your filesystem) and the folders underneath this mount point may still be owned by "root" and be part of the "root" group, rather than "mythtv" for both. You can check this by the command ls -l (that is, "ell") at the level right above where the new drive is mounted. If this mount point is owned or grouped "root" rather than mythtv, then you'll need to use the chown and chgrp commands to switch these over to "mythtv" so that the drive can be correctly accessed.

---

### Post by chipppy on 2009-07-26
Good Afternoon

I have run the ls -l at two level for the mount point of my HDD.

```
chipppy@chipppy-htpc: /mnt/store$ ls -l
total 0
drwxr-xr-x 8 chipppy chipppy 160 2009-07-19 19:52 d2 (blue letters)
```

My understanding is that there is no write allowed to this folder, except root, who can write to this folder.

```
chipppy@chipppy-htpc: /mnt/store/d2$ ls -l
total 0
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:01 LiveTV (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:02 music (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:03 pictures (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:04 poster (green highlighted letters)
drwxrwxrwx 2 chipppy chipppy 6 2009-07-19 20:05 recordings (green highlighted letters)
drwxrwxrwx 8 chipppy chipppy 142 2009-07-19 20:06 videos (blue letters)

```
My understanding is that anyone can do anything to these folders.

/mnt/store/d2/videos is the folder where my DVd rips are located.  At a guess the 'chipppy chipppy' from the print out means that the owner is chipppy.  chipppy is actual my user account so this sound like you are correct and I need to change the owner to mythTV.
Is my guess correct?

Being still a noobie to Linux/gnu how do I change the ownership to mythTV?
I read through a couple of chown and chgrp pages.
Can you please check that I have my understanding is correct for the required commands in terminal and there syntax.

To change ownership and groups of my videos folder do I type the following at the location

```
chipppy@chipppy-HTPC: /mnt/store/d2$ chown -R mythTV videos
chipppy@chipppy-HTPC: /mnt/store/d2$ chgrp -R mythTV videos
```

Or should I change the ownership and group at the next level up 'd2'


cheers
chipppy

---

### Post by klc5555 on 2009-07-26
That's the correct syntax of the command. But chown/chgrp should be run sudo (since root runs owners and groups), and the user/group you're changing to is likely "mythtv", not "mythTV"

You're correct in that likely everything under .../d2 should be owned/grouped by mythtv. And when that is the case, then the permissions should likely be set at 775, rather than wide open at 777, where you have them now. 

But in general if this extra drive is entirely intended to be storage for various aspects of mythtv, it might have been simpler, initially, to have mounted the drive somewhere under /var/lib/mythtv/... where mythbuntu mostly expects extra storage to be set up by default, rather than under /mnt, where temporary mounts tend to reside. But your setup should work just as well, of course.

---

### Post by chipppy on 2009-07-26
Good morning

To clean things up a little I moved my mount point as per you recommendation.  The new hard drive is now mounted at /var/lib/mythtv/hdd2

I also changed the own (sudo chown -R mythtv hdd2).  Below is the new ls -l
```
chipppy@chipppy-htpc:/var/lib/mythtv/hdd2$ ls -l
total 4
drwxrwxrwx  2 mythtv mythtv   70 2009-07-27 09:00 LiveTV
drwxrwxrwx  2 mythtv mythtv    6 2009-07-27 09:00 music
drwxrwxrwx  2 mythtv mythtv    6 2009-07-27 09:00 pictures
drwxrwxrwx  2 mythtv mythtv    6 2009-07-27 09:00 posters
drwxrwxrwx  2 mythtv mythtv    6 2009-07-27 09:00 recordings
drwxrwxrwx 62 mythtv mythtv 4096 2009-07-26 22:38 videos

```

I am still not finding any videos in my video manager.  Below is a couple of screen shots in the hpe that you are able to see something that is wrong so we can finally fix this problem and I can start getting the posters imported

[ATTACH]122549[/ATTACH]

[ATTACH]122550[/ATTACH]

[ATTACH]122551[/ATTACH]

[ATTACH]122553[/ATTACH]

[ATTACH]122554[/ATTACH]

If you want any other screenshots please tell what you need and I will get them for you


Huge thanks for the assistance so far

Cheers
chipppy

---

### Post by crez79 on 2009-07-26
Storage groups are for recorded tv, so you probably should have the LiveTV directory called out specifically. If you aren't using the /var/libs/recordings remove it. This is unrelated, but may help in the future.

Have you verified that the extensions of your videos are not set to be ignored and are specified?
Check the filter when you are in video manager by pressing 'm' and then filter display.
Check the permissions of the videos themselves. If you need to run a sudo chown mythtv:mythtv -Rv /var/lib/mythtv/hdd2/videos and that will change the user:group to mythtv. The R makes it recursive (which you know) and the v will make it verbose so you see exactly what it is doing. 

The owner shouldn't make a difference if the permissions are set like you have them (777) but if the files themselves aren't readable my others, mythvideo won't see anything.

---

### Post by chipppy on 2009-07-27
Good Afternoon

This is the answer to some of the suggestions above

> Have you verified that the extensions of your videos are not set to be ignored and are specified?
I am not totally sure about tis but I found
Utilities/Setup ==> Setup ==> Media Settings ==> Viedo Settings ==> File Types (MythVideos File Associations.
Scrolling around in here I found the following plus a few others.  
```
Extension: iso
Command:   Internal
Use Default: unticked
Ignore: unticked
```
```
Extension: VIDEO_TS
Command:   Internal
Use Default: unticked
Ignore: unticked
```
```
Extension: vob
Command:   Internal
Use Default: unticked
Ignore: unticked
```
```
Extension: avi
Command:   Internal
Use Default: ticked
Ignore: unticked
```
Is this how it is supposed to be or do I need to change something.  I tried changing iso to use default and back to video manager but still no videos found.
[ATTACH]122572[/ATTACH]


Video manager filter setting as per defualt
[ATTACH]122571[/ATTACH]

Check of the group and owner of my videos in /var/lib/mythtv/hdd2/videos
at a guess at least one of these should show up.  Please remember this this problem has been here since install.
```
chipppy@chipppy-htpc:/var/lib/mythtv/hdd2/videos$ ls -l
total 36814504
drwxrwxrwx  4 mythtv mythtv         36 2009-07-24 23:27 Atlantis Milo's Return
drwxrwxrwx 37 mythtv mythtv       8192 2009-07-23 22:12 AVI's
drwxrwxrwx  5 mythtv mythtv         64 2009-07-22 01:06 Ben10 Season 1 Disc 1
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 01:02 Ben10 Season 1 Disc 2
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 01:01 Ben10 Season 2 Disc 1
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 01:00 Ben10 Season 2 Disc 2
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:58 Ben10 Season 3 Disc 1
drwxrwxrwx  4 mythtv mythtv         36 2009-07-23 22:01 Ben10 Season 3 Disc 2
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:56 Ben10 Season 4 Disc 1
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:55 Ben10 Season 4 Disc 2
-rwxrwxrwx  1 mythtv mythtv  735068160 2009-02-14 18:56 Beverly Hills Chihuahua.avi
-rwxrwxrwx  1 mythtv mythtv  733900800 2007-09-24 18:12 Bratz.avi
drwxrwxrwx  3 mythtv mythtv         21 2009-07-22 00:55 Care Bears Oopsy Does It
drwxrwxrwx  4 mythtv mythtv         36 2009-07-23 21:51 Care Bears the Movie
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:55 Casper, A haunted Christmas
-rwxrwxrwx  1 mythtv mythtv 3200352256 2009-03-13 13:48 Casper, A Hauted Christmas.iso
-rwxrwxrwx  1 mythtv mythtv 1029483656 2008-01-14 04:44 CURIOUS GEORGE.avi
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:53 DORA Catch the Stars
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:52 DORA Rhymes & Riddles
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:50 DORA Save the Day
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:49 DORA Save the Mermaids
-rwxrwxrwx  1 mythtv mythtv 4294967295 2009-03-14 06:36 Dora the explorer EGG HUNT.iso
drwxrwxrwx  2 mythtv mythtv       4096 2009-07-22 00:49 Enchanted
drwxrwxrwx  4 mythtv mythtv         36 2009-07-23 21:38 Finding Nemo
drwxrwxrwx  4 mythtv mythtv         36 2009-07-24 23:25 Flushed Away
-rwxrwxrwx  1 mythtv mythtv  277284864 2006-03-10 21:10 Goosebumps Chillogy.avi
-rwxrwxrwx  1 mythtv mythtv  732537668 2009-03-12 14:30 Happily Never After 2.avi
-rwxrwxrwx  1 mythtv mythtv 1023117442 2007-12-09 04:52 Happily Never After.avi
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:46 Heffalump, Halloween Movie
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:46 Hi-5, Hi Energy
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:45 Hi-5, Travelling Circus
drwxrwxrwx  4 mythtv mythtv        116 2009-07-23 21:34 Home Movies
-rwxrwxrwx  1 mythtv mythtv  734781440 2008-04-11 22:49 horton hears a who.avi
-rwxrwxrwx  1 mythtv mythtv  366872576 2009-01-14 08:32 Hulk vs Wolverine.avi
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:44 Ice Age
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:43 Ice Age The Meltdown
-rwxrwxrwx  1 mythtv mythtv  734518154 2009-01-10 15:28 Igor.avi
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:40 Jimmy Neutron, Attack of the Twonkies
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:41 Jimmy Neutron boy genius
drwxrwxrwx  4 mythtv mythtv         36 2009-07-24 23:23 Jimmy Neutron Confusion Fusion
drwxrwxrwx  2 mythtv mythtv          6 2009-07-22 00:40 Jimmy Neutron, King of Mars
drwxrwxrwx  4 mythtv mythtv         36 2009-07-23 21:31 Kung Fu Panda
drwxrwxrwx  4 mythtv mythtv         36 2009-07-24 23:21 Lavender Castle Volume 1
drwxrwxrwx  4 mythtv mythtv         36 2009-07-23 21:29 Lavenrcastle 1
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:40 Little Red Tractor, enter the Dragon
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:39 Madagascar
-rwxrwxrwx  1 mythtv mythtv  734892032 2009-01-25 10:39 Madagascar Escape 2 Africa.avi
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:39 Mickey Mouse Clubhouse, Great clubhouse hunt
-rwxrwxrwx  1 mythtv mythtv  786445642 2009-06-04 05:22 Night at the museum 2.avi
-rwxrwxrwx  1 mythtv mythtv  735326208 2008-12-08 11:32 Open Season 2.avi
-rwxrwxrwx  1 mythtv mythtv 2632044544 2009-07-13 18:22 Piglets big adventure.iso
-rw-rw-rw-  1 mythtv mythtv 6099533824 2009-07-15 14:26 PINK.iso
drwxrwxrwx  3 mythtv mythtv         21 2009-07-23 21:25 SaHara
-rwxrwxrwx  1 mythtv mythtv  731859382 2008-09-29 04:56 Scooby Doo and the Goblin King.avi
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:38 SharkTale
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:36 Shrek
-rwxrwxrwx  1 mythtv mythtv  644017140 2008-02-15 05:47 Snow Buddies.avi
-rwxrwxrwx  1 mythtv mythtv  734969856 2009-01-21 12:39 Space Buddies.avi
-rwxrwxrwx  1 mythtv mythtv  774888646 2008-10-09 16:47 space chimps.avi
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:35 Spirit, Stallion of the Cimarron
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:34 Surfs Up
-rwxrwxrwx  1 mythtv mythtv  733325312 2007-08-15 20:20 Teenage Mutant Ninja Turtles I.avi
-rwxrwxrwx  1 mythtv mythtv  731129856 2007-08-15 17:07 Teenage Mutant Ninja Turtles II.avi
-rwxrwxrwx  1 mythtv mythtv  731385356 2007-08-14 16:47 Teenage Mutant Ninja Turtles III.avi
-rwxrwxrwx  1 mythtv mythtv  733757440 2007-08-15 23:22 Tennage Mutant Ninja Turtles 2007.avi
drwxrwxrwx  3 mythtv mythtv         21 2009-07-22 00:33 The Iron Giant
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:32 The land before time The stone of cold fire
drwxrwxrwx  3 mythtv mythtv         21 2009-07-22 00:31 The Pirates Who Don't Do Anything, a Veggie Tales Movie
drwxrwxrwx  3 mythtv mythtv         21 2009-07-22 00:30 The Secret Nimh 2
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:29 The Tigger Movie
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:27 The Wild
-rwxrwxrwx  1 mythtv mythtv 3325624320 2009-03-13 14:15 Tinkerbell.iso
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:27 TMNT
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:24 TMNT Season 2, Disc 10, Secert Origins
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:25 TMNT Season 2, Disc 9, Turtles in Space
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:23 TMNT, The ultimate Ninja
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:23 Toy Story
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:20 Tractor Tom, Baa Baa Tom Sheep
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:19 Tractor Tom, Baa Baa Tom Sheep & Other Stories
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:18 Tractor Tom, Buzz to the Rescue
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:17 Tractor Tom, Buzz to the Rescue B
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:16 Tractor Tom, Hide & Seek
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:22 Tractor Tom - Sports Day & Other Stories
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:15 Tractor Tom, The New Scarecrow & others stories
drwxrwxrwx  4 mythtv mythtv         36 2009-07-22 00:14 Tractor Tom, The New Vehicle

```

Any and all suggestions welcome and I will try to work through them as quickly as possible

Cheers
chipppy

---

### Post by newlinux on 2009-07-27
Have you looked at your frontend log output when going into video manager? That my help diagnose the error... And I recommend turning up the verbosity of your logging for mythfrontend.

---

### Post by crez79 on 2009-07-27
Maybe try to remove and reinstall mythvideo or do a dpkg-reconfigure mythvideo. Maybe something didn't install right. But checking the logs is a great idea.

---

### Post by chipppy on 2009-07-27
Good Morning

How do I > turn up the verbosity of your logging for mythfrontend?

I gathered the logs and viewed.  I found this information after running the Video Manager

The following appear 12 times and related to different videos (this is the one for Tractor Tom, Baa Baa Tom Sheep.  I only cut|paste one in as all the details are the same except the video name.  There was both .vob and .avi video in the list of different video names.
```
==> /var/log/mythtv/mythfrontend.log <==

2009-07-28 08:42:47.150 DB Error (video metadata update):
Query was:
INSERT INTO videometadata (title,director,plot,rating,year,userrating,length,filename,showlevel,coverfile,inetref,browse) VALUES ('Tractor Tom, Baa Baa Tom Sheep', 'Unknown', 'None', 'NR', 1895, 0, 0, '/var/lib/mythtv/hdd2/videos/Tractor Tom, Baa Baa Tom Sheep', 1, 'No Cover', '00000000', 1)
Driver error was [2/130]:
QMYSQL3: Unable to execute query
Database error was:
Incorrect file format 'videometadata'
```
This is the other information that came out of the logs for the Video Manager.
```
2009-07-28 08:42:47.196 XMLParse::LoadTheme using /usr/share/mythtv/themes/blue/video-ui.xml
2009-07-28 08:42:47.406 videolist.cpp: getVideoListMetadata: index out of bounds: 0

2009-07-28 08:42:47.406 DB Error (Querying video metadata):

2009-07-28 08:42:47.406 videolist.cpp: getVideoListMetadata: index out of bounds: 0
```
I dont really understand much of the above so I am hoping that you guys might understand|see and problem that we can look into.

I closed down the frontend, ran dpkg-reconfigure mythvideo, and restarted frontend.  No change
```
chipppy@chipppy-htpc:~$ sudo dpkg-reconfigure mythvideo
[sudo] password for chipppy: 
chipppy@chipppy-htpc:~$
```

Closed down frontend again, via synaptic package manager, completely removed mythvideo, reinstalled mythvideo, started up frontend.  Still no change.

Did a reboot, just incase something needed to happen during the boot process with the removal | install, but still no change.
Does this information helps us out any?

Thanks for the assistance

Cheers
chipppy

---

### Post by newlinux on 2009-07-27
ahhh the infamous 

> 
videolist.cpp: getVideoListMetadata: index out of bounds: 0


Not sure how to fix that one. You could try running a database repair...

You can turn up the verbosity by doing by doing:

```

mythfrontend -v all -l <insert logfile here>

```

or you can modify the 
/etc/mythtv/session-settings

and it will log it to /var/log/mythtv/mythfrontend.log like always....

---

### Post by chipppy on 2009-07-28
Good Moring

How do I run a database repair?

Cheers
chipppy

---

### Post by newlinux on 2009-07-29
[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database)

I think the optimize_mythdb.pl script is in 
/usr/share/doc/mythtv-backend/contrib/
on ubuntu.

---

### Post by mixu75 on 2009-08-01
Hi y'all,

total newbie here, but I did struggle with the same problem as Chipppy here. First there was this darned ol' black box hovering over my Video Library, asking for an IMDB number. Script so graciously provided on the first page of this discussion did away with that.

Then I didn't have the time and the energy to solve the problem with not all of my videos showing in the Video Manager. Hard drive videos showed up, LAN drive videos didn't, but they all did play nice and well under the Video Listings menu. Besides, I had better things to do as a Ubuntu newbie at that point, like figuring out how to make my LAN printer and scanner work smoothly - or at all for that matter.

So I skipped all the hi-tech stuff in the rest of the discussion here and went along doing my business, until I installed Ubuntu and MythTv on my other computer. Basically it was the same installation with the same specifics for frontend/backend MythTV, except this computer was a laptop and connected to LAN via WLAN, in my opinion a bit more unrealiable techwise than the ethernet connection. Anyways, my surprise was that much greater when Video Manager worked fine and found all the videos on my network drive folders.

Back again working with the first computer I did scratch my head for a few hours, installed some Samba packages I thought might be relevant, but nothing. Then it occured to me:

MythTv video settings accept media destinations without the first "/" and they work fine under Video Listing and Video Gallery, but Video Manager won't find those folders.

In other words:

media/mediadrive/movies  -> Video Manager can't read this
/media/mediadrive/movies -> Video Manager can read this

But I'm sure that it was just stupid old me who had a hard time figuring this one out, and Chipppy's problem is something else.

Much obliged, though, for providing food for my thoughts and seeds for my discovery.

---

### Post by chipppy on 2009-08-26
OK 

Sorry I have been away for work for a couple of weeks.
I looked into the / and no /

currently in /var/lib/mythtv/hdd2/videos so doesnt look like that is the problem.  I tried var/lib/mythtv/hdd2/videos just oin case and still no luck getting the listings working under video manager.

I have found that we I added approx 20GB on music files into the correct folder that they also are not found when I try update music database.
Same symptoms but different area.
This means that I am unable to listen to any music.

Does this help anyone with some ideas as to what I can look into to try and get the folder listing working.  

cheers
chipppy

---

