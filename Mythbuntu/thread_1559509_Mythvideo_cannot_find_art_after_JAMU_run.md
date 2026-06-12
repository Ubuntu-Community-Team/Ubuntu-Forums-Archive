---
title: "Mythvideo cannot find art after JAMU run"
date: 2010-08-23
forum: Mythbuntu
---

### Post by Lightsider on 2010-08-23
I'm running MythTV 0.23+fixes (version 24158) on Mythbuntu 9.10. I set up MythTV and everything was working fine - I had added several video files to MythVideo, and had added metadata (and downloaded art) through the MythVideo interface. 

I then ran JAMU to automate the metadata grab. JAMU ran successfully, adding new video files to the MythTV database (MythVideo found them, along with the metadata JAMU had added, so I'm assuming that it went well). JAMU also downloaded art, but MythVideo can't find it. 

When I browse to a video file in MythVideo, the Mythfrontend log shows errors:

```

Unable to find image file: 1271_coverart.jpg
Unable to find image file: 1271_fanart.jpg
```And so on for every file I browse to. What I don't understand is that these files exist in the directories specified in the Mythfrontend (/var/lib/mythtv/coverart, /var/lib/mythtv/fanart etc). Permissions for the directories are set to drwxrwsr-x, and -rw-r--r-- for the files, so MythTV can definitely see them. 

When JAMU runs, it shows the following messages:

```
! Info: You have a front end directory path that is a duplicate of this backend's storage group.
Front end directory (/var/lib/mythtv/screenshots)
The Front end setting has been ignored.

(repeat same for fanart, coverart and banners)

==========================================================================================
Listed below are the types and base directories Jamu will use for processing.
The list reflects your current configuration for the 'kepler' back end
and whether a directory is a 'SG' (storage group) or not.
Note: All directories are from settings in the MythDB specific to hostname (kepler).
Note: Screenshot directories are not listed as Jamu does not process Screenshots.
------------------------------------------------------------------------------------------
Type: Fan art     - SG-YES - Directory: (/var/lib/mythtv/fanart)
Type: Video       - SG-YES - Directory: (/var/lib/mythtv/videos)
Type: Video       - SG-NO  - Directory: (/var/lib/storage/mythtv)
Type: Cover art   - SG-YES - Directory: (/var/lib/mythtv/coverart)
Type: Banners     - SG-YES - Directory: (/var/lib/mythtv/banners)

```So these paths look correct to me, or am I missing something?

And even stranger: MythVideo can find *some* of the art located in /var/lib/mythtv , but not others (all the art it can find was present before I ran JAMU, but not all the art it can't find was added by JAMU, so I can't make heads or tails of this). 

If I "reset metadata" in MythVideo, then download metadata again, everything works. But that means I would have to abandon JAMU, and I would love to get it to work :) 

Concerning the JAMU configuration, I used a copy of jamu-example.conf as my configuration file, leaving everything as default except "**local_language: en"**. Could I have overlooked something in these options?

Where could I start looking for the problem? Can I access the MythTV database directly to see where it's trying to look for the artwork? 

Thanks a lot for all your help! :)

---

### Post by cipitin on 2010-09-05
I have a similar problem, or maybe the same problem.  I'm running mythbuntu 10.04 and executed the JAMU script to populate the metadata for my videos (which seemed to work fine), but the clipart never would display in mythvideo.  However, if I manually download the metadata from inside mythvideo, the coverart will display for awhile but later it will stop displaying.  I have the same errors in my mythfrontend.log file and the directories are correct in my mythvideo setup.  I've tried changing the permissions with no effect. I also had the same JAMU warning about having duplicate front end and back end storage paths for the clipart, fanart, etc.

---

### Post by cipitin on 2010-09-05
Upon further research, it appears that the problem is with using Storage Groups (on the backend) and frontend specified directories.  I went into the backend setup and deleted all of the storage groups for mythvideo related material (fanart, coverart, etc), and then reran the Jamu script to correct the path to the video metadata files relative to the frontend specified directories, and now it appears to display the coverart fine.  Also, inside mythvideo you can edit the metadata for an individual video and see the filename for each image file (coverart, etc).  Before I made this change only the image file name was specified.  After I made this change and reran the Jamu script, the full absolute pathname was also specified with each image name.  Hope this helps.

---

