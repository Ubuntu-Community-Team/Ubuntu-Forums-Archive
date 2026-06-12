---
title: "How to archive recordings?"
date: 2009-02-18
forum: Mythbuntu
---

### Post by zsara on 2009-02-18
Hi, I have a problem archiving the recorded video to the DVD. 
My configuration is: 
a)Server with Mythbuntu backend running
b)Diskless Mythbuntu frontend booting from the server
After many hours everything works ok, except Archiving recordings to the DVD. The problem is there aren't any recordings in the dialog "CD/DVD-Archive-Export-DVD-Recordings". The error message says there aren't any recordings localy accessible. Other 2 buttons (video and file) works. All backend media directories - recordings, video, music and pictures are shared in network via samba. 
Don't You have any idea how to solve it?
Thanks
Zdenek

---

### Post by jMon54 on 2009-02-18
have you looked at: [http://mythtv.org/wiki/MythArchive](http://mythtv.org/wiki/MythArchive)

---

### Post by zsara on 2009-02-18
Yes, after this FAQ I added new row into the table settings:

insert into settings (value, data, hostname) VALUES ('RecordFilePrefix', '/var/lib/recordings/smb_recordings/recordings', '001d602c7e24');

/var/lib/recordings/smb_recordings is the samba mount point,
/var/lib/recordings/smb_recordings/recordings is the full path to the recordings.

001d602c7e24 is MAC of the diskless frontend

---

### Post by zsara on 2009-02-18
Sorry, it works now. I made a mistake when typing a directory. 
:D

---

### Post by zsara on 2009-02-18
Unfortunetly it still doesn't work. Now I can see all recordings in the dialog, I can choose them, but...
During processing the file a stupid error ocures. Look at the twice file name in the path:

---------------------------------------------------------------
2009-02-18 17:09:45 mythburn.py (0.1.20080726-1-fixes) starting up...
2009-02-18 17:10:05 Found 1 CPUs
2009-02-18 17:10:05 Obtaining MythTV settings from MySQL database for hostname 001d602c7e24
2009-02-18 17:10:10 temppath: /var/lib/mythtv/video/work
2009-02-18 17:10:10 logpath:  /var/lib/mythtv/video/logs
2009-02-18 17:10:10 Setting process priority to 17
2009-02-18 17:10:10 Processing Mythburn job number 1.
2009-02-18 17:10:10 Options - mediatype = 0, doburn = 1, createiso = 0, erasedvdrw = 0
2009-02-18 17:10:10           savefilename = ''
2009-02-18 17:10:10 Looking for: /usr/share/mythtv/mytharchive/themes/MythCenter - Autoplay/theme.xml
2009-02-18 17:10:10 Loading font 0, /usr/share/mythtv/FreeSans.ttf size 23
2009-02-18 17:10:10 Loading font 1, /usr/share/mythtv/FreeSans.ttf size 18
2009-02-18 17:10:10 Loading font 2, /usr/share/mythtv/FreeSans.ttf size 16
2009-02-18 17:10:10 wantIntro: 1, wantMainMenu: 0, wantChapterMenu:0, wantDetailsPage: 1
2009-02-18 17:10:10 Final DVD Video format will be pal
2009-02-18 17:10:10 There are 1 files to process
2009-02-18 17:10:15 Pre-processing recording 1: '/var/lib/mythtv/recordings/smb_recordings/recordings/2257_20090105050000.mpg/2257_20090105050000.mpg'
2009-02-18 17:10:15 ************************************************************
2009-02-18 17:10:15 ERROR: Source file does not exist: /var/lib/mythtv/recordings/smb_recordings/recordings/2257_20090105050000.mpg/2257_20090105050000.mpg
2009-02-18 17:10:15 ************************************************************
2009-02-18 17:10:15
2009-02-18 17:10:26 Terminated






















1Pomoc  2Nezal. 3Konec  4Hex    5&#344;ádek  6RxHled 7Hledej 8Hrub&#283;  9Odform.10Konec

---

### Post by zsara on 2009-02-19
Well, I've solved it. :) The problem was the trailing \ in the Storage profile. The \ is automatically added after editing the path. It is nessesary to delete the trailing \ directly in MySQL table storage.

---

