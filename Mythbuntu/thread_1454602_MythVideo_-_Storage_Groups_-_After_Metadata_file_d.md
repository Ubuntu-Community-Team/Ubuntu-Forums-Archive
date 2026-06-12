---
title: "MythVideo - Storage Groups - After Metadata file disappears"
date: 2010-04-14
forum: Mythbuntu
---

### Post by kyfehr on 2010-04-14
I have moved my MythVideos to Storage Group. All went well. Found folders and files ok. 

Once I grab Metadata for the file (this works and updates correctly) if I scan for changes or move to main menu and back in - the file is no longer listed as if it is deleted and gone. The files are not touched they are all sitting there in their folders, but are removed from the database. 

I have tried with no directory listed for videos in the setting page for Videos and with a directory the same as on of the storage groups - same result. in the meantime I am adding back a local directory so I cann have my metadata back.

I need help. The stroage groups are nice because I am trying to setup the whole house and also make it easier to add disk space for my DVD rips.

I am using the .23-fixes from Autobuilds.

UPDATE - just tried to find the files in the  local directory in mythtv and they are not listed there - is this related to Hash tags in .23??? any help would be great. Thank you. Also I am using Arclight for the theme if that matters.

UPDATE 2 - deleted all video storage groups. pointed local directory to blank folder - scanned to remove videos - redirected local directory to /var/lib/mythtv/videos scanned again and the videos came back, but as soon as you do a metadata update and leave screen/scan for changes the file disappears from listing. very very very very frustrating - launching mythfrontend from terminal and not seeing anything out of the ordinary

Now wondering how to reset the hash tags cause i think that is the problem

---

### Post by dannyboy79 on 2010-04-16
if you;re using storage groups, you have to make sure you leave all frontend video locations (all SG locations) BLANK on all frontends. let the frontend be driven by the backend storage groups. You have to run the frontend once on your backend and hit M to scan for changes. then just make sure all your frontends (including the frontend on teh backend) have nothing defined for the folder locations because it's going to use what the Storage Groups are defined as. good luck

---

### Post by TheMiz on 2010-04-20
OK, I have a similar problem, and I don't really want to start a whole new thread for it...

I have 2 frontend only computers and a FE/BE combo.  I want to store my ISO files (I know these do not work with storage groups) on one of the remote frontends, and have the rest of my mp4/vob videos on my backend (and accessible via storage groups).  I only want to view the ISO files on 1 remote FE.

So what should I do to prevent the metadata from resetting on the ISO files every time I scan for changes?  If I leave the video locations blank on all FE's, I can't view the ISO files I have, so I have to add the folder where the ISO's are stored on the remote FE, but I left it blank on the other computers.   Am I making sense?

Thanks for any insight.

---

### Post by dannyboy79 on 2010-04-20
skip any video with a inetref of '99999999'. Meta data and
graphics are all manually entered and should not be altered by Jamu.
Currently used for any meta data that you do not want modified by Jamu.

---

### Post by unkle1 on 2010-04-21
> **kyfehr said:**
> 
UPDATE 2 - deleted all video storage groups. pointed local directory to blank folder - scanned to remove videos - redirected local directory to /var/lib/mythtv/videos scanned again and the videos came back, but as soon as you do a metadata update and leave screen/scan for changes the file disappears from listing. very very very very frustrating - launching mythfrontend from terminal and not seeing anything out of the ordinary

Now wondering how to reset the hash tags cause i think that is the problem

This might not help at all since you're not seeing any errors in the log, but it might be worth a shot. A few days ago the metadata got errorneus on my 10.04b but doing a truncate on the table "videometadata" and running Jamu/scanner again fixed it. (Mysql complained about duplicate entrys in the db but my two cents is to try to reset some of the tables in your database). Also, I think the team wrote something about the SG as being very far from finished so there might (will) be some hickups here and there.

---

### Post by kyfehr on 2010-04-23
figured it out. I don't use JAMU for doing stuff and manually edit videos and retrive the data myself. There were some cron jobs set from the Control Centre that I disabled and now the files aren't disappearing.

---

