---
title: "Questions on my setup and settings"
date: 2008-09-27
forum: Mythbuntu
---

### Post by zalnn on 2008-09-27
Hi all,

I have my Mythbuntu MBA setup. It doesn't have much in terms in storage, so I want all the BEs to store recordings on my storage server.

The storage server is software raid5 and will only hold DVD backups  and recordings. MAYBE my mp3 collection too.
What file system should I use for the storage server? Why?

The MBE holds 2 PVR-150s (for now), its a P4 with 2GB of ram and a 35GB HDD.

I want to have 2 - 3 SBAs.
The 1st SBE is a DELL Poweredge with Dual Xeon processor and 3GB of RAM. I will use this do batch transcoding of the recordings.

The 2nd (and maybe, 3rd) SBE will have more tuners for capturing.

I want to have 2 FEs (bedroom and living room), these would preferably be diskless or the Hauppauge MediaMVP running mvpmc.

[B]Questions
[/B]
1. What is the best way to setup the DELL PowerEdge to do the transcoding? cronjob? Somehow through MythTV MBE? Once a recording is transcoded (into DivX or Xvid) the original would be deleted as a recorded program and stored  under media, instead of recordings.
**EDIT:** I could run mythtranscode to convert to DivX. Could I make mythtranscode CLEANLY remove the original file too?  How would I set things up so that the transcoding is done in batch mode on the SBE?
 
2. Does the storage server need to be mounted on all the BEs and FEs or just the MBE / SBEs?

3. Would it be possible to make the BEs (that capture) capture to its local drive and then move the recording to the storage server after capture is complete, all while keeping the integrity of the MythTV dbase. 

4. When you set the disk limit on the FEs how does it affect the BEs?

Proposed setup (not sure how the storage server needs to be mounted)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86568&stc=1&d=1222529400[/IMG]

Thanks in advance for the help guys...

---

### Post by ian dobson on 2008-09-27
Hi,

**Answers**

1) You can start a transcode job from a frontend. The actual job runs on the backend. Recordings aren't moved about by mythTV.

2) You don't need to mount everything everywhere. If you want to transcode from one backend on another you need to have the storage mounted.

3) I don't think so.

4) What do you mean by "disk limit"?

Regards
Ian Dobson

---

### Post by zalnn on 2008-09-28
> 
1) You can start a transcode job from a frontend. The actual job runs on the backend. Recordings aren't moved about by mythTV.

Which BE does it start on?  Can jobs be forced to run on a specific BE?

> 3) I don't think so.
I could write a script that moves the recording off the local HDD to the storage server.
> 
4) What do you mean by "disk limit"?

On the FE you can set the a parameter so that MythTV leaves that much free space on the HDD so that the HDD doesn't fill up all the way. So if you have multiple directories setup how does this setting affect all the directories?

---

### Post by ian dobson on 2008-09-28
Hi,

1) I think the transcode will start on the backend that "owns" ie has it local. I think you can force myth backend to use any available backend.

3) You could write a user job to move the file/update the recorded database.

4) Myth backend will try and keep the minimum amount of space free on all storage groups by storing recordings on the best possible storage group.

Regards
Ian Dobson

---

### Post by zalnn on 2008-09-29
> 
3) You could write a user job to move the file/update the recorded database.

Where can I find more information about updating the database that holds information about recordings? 
1. clearing out recordings that have been deleted 
2. updating the database to point to the new location of a moved recording?

Thank you for the patients and help Ian.

-Joseph

---

### Post by ian dobson on 2008-09-29
Hi,

Have a look for the documentation for the mythtv perl bindings.

I've never used it myself, I always go directly into the SQL database.

Regards
Ian Dobson

---

