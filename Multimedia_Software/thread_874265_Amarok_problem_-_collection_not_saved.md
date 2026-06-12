---
title: "Amarok problem - collection not saved"
date: 2008-07-29
forum: Multimedia Software
---

### Post by Sonolin on 2008-07-29
Hello,

I have a problem with Amarok.  For some reason, no matter what settings I put, Amarok never saves my collection.  It saves my playlists but not my collection.  So, if I want to browse my collection (through search, etc.) it doesn't work - I have to rescan it each time I start up Amarok.

At first I thought it may be a problem with me using MySQL instead of SQLite, but I switched to SQLite and the problem persists.  This is really odd I believe it should automatically save the collection.  I am using Amarok 1.4.7

Something also strange is if I use MySQL then Amarok does not remember my marked collection folder.  However, if I switch to SQLite it does remember my collection folder (but I still have to rescan).

My music files are on an NTFS partition which has Windows Vista installed if this may affect it, I am not sure if Amarok has problems with NTFS.  If so this would be an easy fix because I am getting a new hard drive soon that I will make ext3 to use as my home partition and any windows program files.

Thank you for any help you can offer, let me know if you need to know any information (I can post my MySQL database if you would like).  I am no stranger to computers, only a couple years of linux experience but I feel comfortable in a linux environment.

EDIT: By the way, I have tried manually clicking the "Quit" option - I read somewhere that it may be a problem when ubuntu ends processes on restart/shutdown so this eliminates that option.

EDIT EDIT: I don't think this would matter but I am on Ubuntu 7.10, possibly upgrading when I get my new hard drive

EDIT EDIT EDIT: Sorry sorry everything is solved!  I indeed did switch to SQlite and it is working now.. don't know why it wasn't working before!  I will look into mysql later if I really feel like I need it.

---

