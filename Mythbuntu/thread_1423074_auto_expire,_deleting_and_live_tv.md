---
title: "auto expire, deleting and live tv"
date: 2010-03-06
forum: Mythbuntu
---

### Post by My Name on 2010-03-06
Hi folks,
So, auto expire... does it delete the files?
Sounds like it should but I have a small 36GB solid state system drive which I want to use to store live tv, as I don't want to fill a large drive with live tv files.
The problem I'm having is that the drive just keeps filling up which borks the system.
I haven't changed a great deal of the default settings in both the frontend and the backend. surly it should be fairly strait forward to have the machine delete live tv shows automatically. 
I'm going to do a fresh install one last time to clean up the database. Could somebody please advise me on some setting which will make sure the drive no longer fills up.
oh i'm using 0.22 BTW
Thanks

---

### Post by tgm4883 on 2010-03-06
> **My Name said:**
> Hi folks,
So, auto expire... does it delete the files?
Sounds like it should but I have a small 36GB solid state system drive which I want to use to store live tv, as I don't want to fill a large drive with live tv files.
The problem I'm having is that the drive just keeps filling up which borks the system.
I haven't changed a great deal of the default settings in both the frontend and the backend. surly it should be fairly strait forward to have the machine delete live tv shows automatically. 
I'm going to do a fresh install one last time to clean up the database. Could somebody please advise me on some setting which will make sure the drive no longer fills up.
oh i'm using 0.22 BTW
Thanks

Well live TV and recorded TV are the same thing. It shouldn't be filling the drive. Autoexpire allows the recordings to be deleted when there isn't enough free space on the drive (a setting you can set in the storage group section of mythtv-setup I think).

MythTV will automatically delete recordings when it needs space based on a priority. LiveTV gets deleted first.

---

