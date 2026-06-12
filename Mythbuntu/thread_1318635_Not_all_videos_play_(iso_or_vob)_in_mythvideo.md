---
title: "Not all videos play (iso or vob) in mythvideo"
date: 2009-11-07
forum: Mythbuntu
---

### Post by williammanda on 2009-11-07
As the title states not all videos play in mythvideo (mythtv .22). All videos that are in question were ripped using mythtv .21 either iso or vob. Also I don't have a video storage group. I export the videos using nfs to the slave backend. This isn't a permission issue. Here is the FE log of a vob video that can't be played:

```
2009-11-07 18:24:04.355 TV: Attempting to change from None to Watching Video
2009-11-07 18:24:04.670 TV: StartPlayer(0, Watching Video, main) -- begin
2009-11-07 18:24:04.882 RingBuf(myth://Videos@192.168.1.100:6543//var/lib/mythtv/videos/Antz.VOB) Warning: Peek() requested 2048 bytes, but only returning 0
2009-11-07 18:24:04.882 NVP::OpenFile(): Error, couldn't read file: myth://Videos@192.168.1.100:6543//var/lib/mythtv/videos/Antz.VOB
2009-11-07 18:24:04.882 TV: StartPlayer(0, Watching Video, main) -- end error
2009-11-07 18:24:04.903 ScreenSaverX11Private: DPMS Deactivated 1
2009-11-07 18:24:22.858 AudioPulseUtil: Resume Success
2009-11-07 18:24:22.863 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit
2009-11-07 18:24:28.264 ScreenSaverX11Private: DPMS Reactivated 1
```

Thanks

---

### Post by SiHa on 2009-11-08
If you unmount the nfs shares, can you still play the videos (that do play normally)?

I didn't set-up storage groups when I installed 9.10, but I tried unmounting my nfs shares from the frontend (to test a theory on another problem), and my videos still play (except the .iso's). I think the backend install must default to SG's by default. Even if the folders are available locally via nfs, they will be ignored if the same path is available via the storage groups.

I think```
myth://Videos@192.168.1.100:6543//var/lib/mythtv/videos/Antz.VOB
```Indicates that storage groups are in use.

Edit: **To disable storage groups for Videos**

Backend setup > Storage Directories. Select 'Videos' and delete '/var/lib/mythtv/videos'. The entry will default to '/'.

When exiting the setup, it will complain that '//.test/' cannot be written, select 'No thanks, I know what I'm doing'.

In the frontend, Utilitites/Setup > Setup > Media Settings > Media Settings > Video Settings > General, check 'Directories to hold videos' is showing the correct path to the nfs share.

In 'Watch Videos', press 'M' and scan for changes. All videos should be available again, and your .iso's should play.

Cheers,

Simon

---

### Post by williammanda on 2009-11-08
Thanks for the reply SiHa but I don't have video storage group enabled on either backend (this was stated in my original post). It is the only one I removed and all the other storage groups are still enabled. Other facts:
1. Of the videos that play in mythtv, they have no metadata. The ones that don't play, have metadata. This goes for iso or vob videos.
2. All vob videos play using several media players: xine, mplayer, gnome mplayer and movie player. I can't find a media player that will play iso, so I can't test that yet.
3. I copied a vob video into /var/lib/mythtv/videos yesterday. Added the metadata and viewed the video with mythvideo. Today I can't view the same video. I get the same error as with the antz.vob stated in my previous post. I haven't made any changes to mythtv.
 
If this indicates that storage groups is in use:

```
myth://Videos@192.168.1.100:6543//var/lib/mythtv/videos/Antz.VOB
```

then I have a problem since there isn't an entry for video in storage groups.

---

### Post by SiHa on 2009-11-08
Sorry, I did read that you said you weren't using storage groups. But I wasn't intentionally, either. Just checking that you hadn't overlooked the same thing I did!> 
If this indicates that storage groups is in use:

```

myth://Videos@192.168.1.100:6543//var/lib/mythtv/videos/Antz.VOB
```

then I have a problem since there isn't an entry for video in storage groups.

Well it certainly looks to me like it's attempting to stream from the backend. I only get lines like this when that is happening. When playing a locally mounted video, I don't. But, whatever. The metadata thing looks a little odd, so I'm probably barking up the wrong tree.

---

### Post by williammanda on 2009-11-08
OK problem resloved! I went over to #mythtv-users and found the answer. Apparently I ran a version of Jamu on my videos that was broken. I needed to clear the metadata and reload it to get the files to play, and not run Jamu on them again until it has been updated. You need reset the filename/host, you can't do this by resetting the metadata. You will need to have an empty video directory and scan to accomplish this. I renamed /var/lib/mythtv/videos to /var/lib/mythtv/videosold and created a new /var/lib/mythtv/videos directory (this created an empty directory). I then started mythtv> video> video manager and scanned the directory. I closed mythtv and reversed the /var/lib/mythtv/videos change I did previously. Started mythtv> video> video manager and scanned the directory again and went through all the videos and setup the metadata.

---

### Post by SiHa on 2009-11-09
Interesting!

Does that mean the version of JAMU that ships with 9.10 is broken?

---

### Post by utar on 2009-11-09
I have just spent the last 45 mins trying to work out why some of my video directories had stopped working and I got the same error messages in my log which made me think that Myth was trying to use storage groups for some reason.

Anyway I noticed from my logs that jamu had run earlier and was starting to think this caused the problem.

Good to have some confirmation.  Any news on an updated version of jamu or should I disable the cron jobs?


Utar

[Edit: I have disabled jamu running automatically, as I don't want to have to fix things again.  Slightly OT but I use [http://code.google.com/p/fill-mythvideo-metadata/](http://code.google.com/p/fill-mythvideo-metadata/) for automatic metadata downloads which works very well for both TV shows and movies]

---

### Post by williammanda on 2009-11-09
Utar
How did you disable jamu from running automatically? My original issue came back again.

---

### Post by utar on 2009-11-09
Delete (or move) the mythvideo files from:

/etc/cron.hourly
/etc/cron.daily
/etc/cron.weekly

I personally moved the files to my home directory in case I want to put them back in the future.


Utar

---

### Post by williammanda on 2009-11-11
Can anyone comment on when this will be fixed?

---

### Post by RDV on 2009-11-23
As far as the Jamu part of this thread is concerned Mythbuntu 9.10 shipped with a RC candidate of MythTV. There was a bug in Jamu that appeared when users mixed storage groups and FE settings for image directories.

This was fixed for the official MythTV 0.22 release among a number of other fixes for MythTV. You can get all the latest updates to 0.22+fixes. Follow the instructions at [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

Considering both Mythbuntu and MythTV 0.22 are new keeping up to date would be prudent.

---

### Post by rich86 on 2009-11-25
Hi, i had this same issue caused by running JAMU and it not reconising i wasn't using Storage Groups. I did find a much easier fix that lossing all the video metadata and moving files around.

All i did was enter the mythtv database (mythconfig for me) in MySQL Query Editor went to display the table 'videometadata'. I noticed that all the videos JAMU had updated the metadata for a value for the host in the table had been added. I just removed all the 'host' values back to blank by running 
```
UPDATE videometadata SET host=''
```
This will set the host back to blank for ALL videos in the database. BE CAREFUL IF SOME VIDEOS ARE USING STORAGE GROUPS [TAKE A BACKUP FIRST].
I restarted the frontend and all was well again. I have even kept all metadata covers fanart etc.

Hope that helps anyone else that has this problem. PM or reply if you still have a problem or want more help.

---

### Post by debenbain on 2010-02-15
Thank you for the information. I had tried to use storage groups for a library containing ISO's and discovered the playback limitation:
"ISO/VIDEO_TS Playback does not presently work in Storage Groups"
[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide)

I had deleted the video storage group but kept the groups for fanart and cover images. My solution to limited storage space deleted all of my metadata, which is why I used Jamu. That is when a discovered the Jamu bug mentioned above.

[LIST]
[*]The Mythbuntu auto-builds have updated Jamu.
[*]I deleted the fanart and cover image storage groups (video group was delete already). You cannot mix storage groups and fixed directories.
[*]Clearing the host column will allow the videos to play again.
[*]You will need to add the full directory path to the fanart and coverfile columns to get your cover images back.
[/LIST]

MythTV is not a destination, but a journey ;)

---

### Post by dison4linux on 2010-03-22
Not to hi-jack this thread, but.....

Regarding Storage Groups, I have read about the issues involved in the new Storage Groups and how they are not yet working with ISOs and VIDEO_TS folders, and I am currently using the workaround successfully.  When you go to videos on mythweb it says that you must use Storage Groups.   My question is, will the Storage Group not recognizing ISOs and VIDEO_TS folders issue going to be fixed by release, or will it simply not be possible to use mythweb to browse/edit your videos if they are ISOs/VIDEO_TS folders?

---

