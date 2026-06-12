---
title: "Videos &amp; Automatic Video Recordings"
date: 2010-08-23
forum: Mythbuntu
---

### Post by Anoxymous on 2010-08-23
I am trying to understand how stored videos work in mythbuntu but I cant seem to figure it out so I am looking for answers to a few questions.

[B]Question 1: How do I browse my own media folders?
[/B]I added symbolic links into the /var/lib/mythtv/videos/ folder went into "Media Library"->"Watch Videos" pressed m & scanned. The folders I wanted appeared in the root/base folder (well except the ones without videos in them). But then later when I added files to those folders i scanned for updates and it then came up with a "storage folder" & "videos". The "storage" folder seems to contains all the files from my movies folder where the "videos" folder contains all the other folders (except the movies one) that use to appear on the base folder. Each time i update scan it toggles between this & I don't understand why.

[B]Question 2: Where did my recorded show get stored?
[/B]I set up a recording of a show which seemed to work properly. It automatically switched to the show when it came on & if i tried to change channels it said it couldn't cause it was recording. I later wanted to watch the show & checked under the "Media Library"->"Watch Recordings". To my surprise i found lots of shows from the last 30 hours that had been recording since i set it up. I researched a little to find LiveTV is automatically recorded & stored as u watch it but there wasn't much info on it (which leads to question 3). My recorded show was not there however. Where did it go?

[B]Question 3: How does the Automatic Video Recording of Live TV Work?
[/B]I understand that it records by shows that u watch but I was wondering about storage. i read somewhere that it will delete older files when the hard drive is full. is there a way to designate how much storage space can be used for this recording rather then when the disk is full? in case i want disk space for other applications? When it deletes old videos will it only delete the automatic recordings or will it delete the videos in my other folders too? Will it delete videos I have scheduled to record? If something automatically recorded can i save it somewhere more permanent?

---

### Post by tgm4883 on 2010-08-23
> **Anoxymous said:**
> I am trying to understand how stored videos work in mythbuntu but I cant seem to figure it out so I am looking for answers to a few questions.

[B]Question 1: How do I browse my own media folders?
[/B]I added symbolic links into the /var/lib/mythtv/videos/ folder went into "Media Library"->"Watch Videos" pressed m & scanned. The folders I wanted appeared in the root/base folder (well except the ones without videos in them). But then later when I added files to those folders i scanned for updates and it then came up with a "storage folder" & "videos". The "storage" folder seems to contains all the files from my movies folder where the "videos" folder contains all the other folders (except the movies one) that use to appear on the base folder. Each time i update scan it toggles between this & I don't understand why.


Don't stick symlinks to that folder, instead either use mythvideo storage groups, or use the multiple directory format for the frontend mythvideo dir.

If you are using mythvideo storage, you add multiple directories in mythtv-setup.

If you are using legacy frontend settings, you would add multiple directories like this.

```
/path/1:/path/2
```

> **Anoxymous said:**
> 
[B]Question 2: Where did my recorded show get stored?
[/B]I set up a recording of a show which seemed to work properly. It automatically switched to the show when it came on & if i tried to change channels it said it couldn't cause it was recording. I later wanted to watch the show & checked under the "Media Library"->"Watch Recordings". To my surprise i found lots of shows from the last 30 hours that had been recording since i set it up. I researched a little to find LiveTV is automatically recorded & stored as u watch it but there wasn't much info on it (which leads to question 3). My recorded show was not there however. Where did it go?
[QUOTE]

Thats odd, although sounds like you are viewing the livetv group. Hit M and try changing to the default group.

[QUOTE=Anoxymous;9755294]
[B]Question 3: How does the Automatic Video Recording of Live TV Work?
[/B]I understand that it records by shows that u watch but I was wondering about storage. i read somewhere that it will delete older files when the hard drive is full. is there a way to designate how much storage space can be used for this recording rather then when the disk is full? in case i want disk space for other applications? When it deletes old videos will it only delete the automatic recordings or will it delete the videos in my other folders too? Will it delete videos I have scheduled to record? If something automatically recorded can i save it somewhere more permanent?

It actually deletes old shows in order to keep a configurable amount of free disk space, which I believe is 1GB by default. It has a priority of what shows to delete first. I believe it always does livetv recordings first, then watched shows, going from oldest to newest. It will only delete recordings, not anything in mythvideo.

---

### Post by Anoxymous on 2010-08-24
Thanks a lot for your reply. I just have a few more small questions.

How do I set the amount of disk space for live TV Recordings?

How do I specify which folder to put things I record in?

Where is the remote control configuration file stored?
When I start my computer some of the buttons on my remote work they are just not configured appropriately. I wrote a config (.lircrc) and put it in my home directory but it didnt help so killed all lirc processes &  re-installed lirc and it worked. How ever when i restart the buttons are in the old configuration and i need to kill all lirc processes & start lirc to get it working properly.

---

### Post by LowSky on 2010-08-25
From the MythTV backend (option #6 Storage Directories) you can add or change the directories to which things record. Make sure the folder already exist and that the MythTV user can read and write to them. 

As for Live TV space, the frontend has settings for that, I'm not to sure of the path.

LIRC keeps its settings here:
/etc/sysconfig/lirc 

you may beed to edit it to get the buttons to work the way you wish.

---

### Post by petatkinson on 2010-08-31
There are only 5 Options on the Backend main menu.The last thing I need to amend is where LiveTV recordings are stored.The default storage is /var/lib/mythtv/livetv but I can see no section where this can be amended

---

### Post by tgm4883 on 2010-08-31
> **petatkinson said:**
> There are only 5 Options on the Backend main menu.The last thing I need to amend is where LiveTV recordings are stored.The default storage is /var/lib/mythtv/livetv but I can see no section where this can be amended

What version of mythtv are you using? If you keep pressing down, does it go to #6?

---

### Post by petatkinson on 2010-08-31
0.23.Thanks I'll give it a go

---

