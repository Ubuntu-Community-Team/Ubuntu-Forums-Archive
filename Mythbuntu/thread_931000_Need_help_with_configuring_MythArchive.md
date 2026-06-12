---
title: "Need help with configuring MythArchive"
date: 2008-09-26
forum: Mythbuntu
---

### Post by bmwman on 2008-09-26
:confused: I have HTPC with the latest Mythbuntu 8.04.1. Most things work fine but today i tried to burn one of my movies to DVD for a friend and that didn't work. I've never tried it before. I have not changed anything in the settings so it's all the default. I went to Optical disks-Archive-Burn DVD and added the file that I wanted, selected menu theme, SP quality and then Finish. The screen just sits there at the log viewer and nothing happens at all. I looked at the backend and frontend logs in /var/log/mythtv but there is no info regarding the transcoding. 

Is there any scripts or any settings that I need to set in order to burn a movie to DVD?

Thanks in advance.:

---

### Post by bmwman on 2008-09-26
Actually i figure it out myself - the /var/lib/mytharchive/temp folder didn't exist so I just created it and set up the correct permissions.


P.S. Well, next problem came up. Everything seemed to finish fine, the transcoding, the disk was burned, etc. When I tried to play it though, it doesn't work. I tried it on my laptop and the disk looks empty with label the name of the movie. What is wrong now?

---

### Post by bmwman on 2008-09-26
I think the problem is when burning the DVD. I checked the /var/lib/mythwarchive/temp folder and there is the work dvd folder and contains the video_ts and audio_ts folders and i can play the .VOB files. Then I tried burning another disk second time with Gnome baker and just put the 2 folders on the disk. After it burned "successfully" the disk still looks empty when I check it on my laptop. DVD won't play in any machine.

Any ideas why is this happening?

---

### Post by anonymousdog on 2008-09-27
Windows laptop?  Probably the notorious growisofs version problem.  It's been discussed recently.

---

### Post by ian dobson on 2008-09-27
Hi,

Have a look here [http://ubuntuforums.org/showthread.php?t=918123&highlight=growisofs](http://ubuntuforums.org/showthread.php?t=918123&highlight=growisofs)  I had the same problem and installing the updated growisofs solved the problem.

Regards
Ian Dobson

---

### Post by bmwman on 2008-09-27
I did that and got this error:
> 
 99.56% done, estimate finish Sat Sep 27 09:12:48 2008
 99.95% done, estimate finish Sat Sep 27 09:12:49 2008
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 10434
Path table size(bytes): 90
Max brk space used 0
1290685 extents written (2520 MB)
/dev/dvd: flushing cache
/dev/dvd: updating RMA
/dev/dvd: closing disc
/dev/dvd: reloading tray
:-( unable to reload tray: Input/output error
------------------------------------------------------------
ERROR: Failed while running growisofs.
Result 1, Command was: growisofs -dvd-compat  -Z /dev/dvd -dvd-video -V "Untraceable" /var/lib/mytharchive/temp/work/dvd
Please check the troubleshooting section of the README for ways to fix this error
------------------------------------------------------------

chmod: changing permissions of `/var/lib/mytharchive/temp/': Operation not permitted
Terminated

---

### Post by bmwman on 2008-09-27
OK, after I installed genisoimage_1.1.8-1+b1_i386.deb i keep getting errors. I tried creating ISO instead of wasting another DVD and still the same:
> 
INFO: dvdauthor creating table of contents
INFO: Scanning /var/lib/mytharchive/temp/work/dvd/VIDEO_TS/VTS_01_0.IFO
INFO: Creating menu for TOC

STAT: Processing /usr/share/mythtv/mytharchive/intro/ntsc_mythlogo_intro.mpg...
WARN: attempt to update aspect ratio from 16:9 to 4:3; skipping

INFO: Video pts = 0.500 .. 7.473
INFO: Audio[0] pts = 0.500 .. 8.212

STAT: Processing /var/lib/mytharchive/temp/work/menu-1.mpg...
STAT: VOBU 28 at 2MB, 3 PGCS
INFO: Video pts = 0.178 .. 15.159
INFO: Audio[0] pts = 0.178 .. 30.226
INFO: Audio[32] pts = 0.178 .. 0.178
STAT: VOBU 42 at 3MB, 3 PGCS
INFO: Generating VMGM with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 16:9
INFO: Resolution: 720x480
INFO: Audio ch 0 format: ac3/2ch, 48khz drc

STAT: fixing VOBU at 1MB (17/42, 38%)
STAT: fixing VOBU at 2MB (33/42, 76%)
STAT: fixed 42 VOBUS                         
Finished  dvdauthor
Creating ISO image
sh: mkisofs: not found
************************************************************
ERROR: Failed while running mkisofs.
Command was mkisofs -dvd-video  -V "Untraceable" -o /var/lib/mytharchive/temp/work/mythburn.iso /var/lib/mytharchive/temp/work/dvd
************************************************************

chmod: changing permissions of `/var/lib/mytharchive/temp/': Operation not permitted
Terminated
The permissions of that folder are read/write for group mythtv and others so I don't understand why it's trying to change permissions either.

At least before it was working now it got even worse :(

---

### Post by bmathis on 2008-09-27
I had the same problem with permissions... a work around is giving 777 permissions to the mytharchive folder where it does its work

---

### Post by emshains on 2008-09-27
You have libdvdcss2, haven't you ?

Still, dvd's just don't work for some of us, I've tried to get my dvd playback working for weeks with no successful result other than a headache.

---

### Post by anonymousdog on 2008-09-27
On my system the error in post #6 was fixed with some arguments to growisofs that were included in mytharchive 0.21.0+fixes18207-Oubuntu4~hardy1 (hardy-backports), '-use-the-force-luke=notray'.  I'm betting the DVD created on that run plays in most hardware players and MythTV.

The error in post #7 sorta looks like a missing growisofs.  Do you have dvd+rw-tools installed?  It includes growisofs and is supposed to be a dependency of mytharchive.

The permissions thing isn't a big deal; it's complaining b/c mytharchive runs as the interactive user and expects ownership of the folder.  I made the myth frontend user the owner of /var/lib/mytharchive/temp (and mythtv the group) with 2775 mode so that subfolders and files always have mythtv group ownership...works fine.

---

### Post by bmwman on 2008-09-28
> On my system the error in post #6 was fixed with some arguments to growisofs that were included in mytharchive 0.21.0+fixes18207-Oubuntu4~hardy1 (hardy-backports), '-use-the-force-luke=notray'. I'm betting the DVD created on that run plays in most hardware players and MythTV.
The transcoding is working fine and if I manually burn the Video-ts and Audio-ts from the work folder to a DVD, it does work.

> The error in post #7 sorta looks like a missing growisofs. Do you have dvd+rw-tools installed? It includes growisofs and is supposed to be a dependency of mytharchive.
Everything should be installed because it was working until I upraded to genisoimage_1.1.8-1+b1_i386.deb. Now it doesn't burn or create ISO at all. Before it was working and completes "successfully" but the the disk wouldn't play.
> The permissions thing isn't a big deal; it's complaining b/c mytharchive runs as the interactive user and expects ownership of the folder. I made the myth frontend user the owner of /var/lib/mytharchive/temp (and mythtv the group) with 2775 mode so that subfolders and files always have mythtv group ownership...works fine.
I wasn't getting this error before I upgraded to to genisoimage_1.1.8-1+b1_i386

---

### Post by anonymousdog on 2008-09-28
What version of mytharchive are you on?  I still strongly suspect the fixes version above would help you.

What is the output of 'which growisofs'?  Do you have dvd+rw-tools installed?

Again, the permissions issue is an annoyance; I've seen that whether mytharchive was working or not.

---

### Post by bmwman on 2008-09-28
> **anonymousdog said:**
> What version of mytharchive are you on?  I still strongly suspect the fixes version above would help you.

What is the output of 'which growisofs'?  Do you have dvd+rw-tools installed?

Again, the permissions issue is an annoyance; I've seen that whether mytharchive was working or not.

I'm not sure what version of Mytharchive do I have. It's the one the came with 8.04.1 the official disk.

---

### Post by anonymousdog on 2008-09-29
'dpkg -s mytharchive | grep -i version' will tell you.  I had to hack mythburn.py until fixes18207.
'`which growisofs` -version' will tell you version info on growisofs (and genisoimage) being used on your system.
I'd update your system with update-manager before working too hard on it; the CD-ROM version of mytharchive was broken for me.

---

### Post by klc5555 on 2008-09-29
> **bmwman said:**
> OK, after I installed genisoimage_1.1.8-1+b1_i386.deb i keep getting errors. I tried creating ISO instead of wasting another DVD and still the same:

The permissions of that folder are read/write for group mythtv and others so I don't understand why it's trying to change permissions either.

At least before it was working now it got even worse :(


Mytharchive seems to avoid these permissions problems if you define your mytharchive working temporary directory under your own home directory, e.g. /home/<you>/mytharchivetemp or some such, rather than where the default wants to put it, under /var/lib/mythtv/... It also seems safer than changing myth directory permissions to 777 from the perhaps more reasonable 775. Since the folder's files get completely deleted and rewritten for each archive job, the folder never gets much bigger than for its first job.

Of course, there are still a skazillion other ways for mytharchive to fail in 0.21, which seems to have broken as much as it fixed, but one problem at a time.

Good luck! :)

---

### Post by dannyboy79 on 2008-09-29
this is related in a way. I am still using Mythtv 20.02-fixes (i think) with Feisty Fawn Ubuntu. I recently tried doing this as well and for some reason I put a cd in the  dvd-writer instead of a dvd (silly me), well the log window starting filling up with info and all looked well but when I looked at it a couple hours later it was still at the same spot (process.log file here: [http://pastebin.com/m30f42ece](http://pastebin.com/m30f42ece)) I tried canceling the process and it says it may take a couple minutes to cancel. I waited for hours (still stayed at same process log screen, so I restarted mythtv, restarted my machine but to no avail, whenever I try to go back to create a different mytharchive dvd, it doesn't give me an option to chose which files to archive, it just goes straight to that same filled in log file screen. I just noticed there are these 2 files within the mytharchive folder: mythburncancel.lck  mythburn.lck, do I need to delete these? Also, here is the mythburn.log file: [http://pastebin.com/m27c3f444](http://pastebin.com/m27c3f444)

Any help would be appreciated.

---

### Post by klc5555 on 2008-09-29
> **dannyboy79 said:**
> this is related in a way. I am still using Mythtv 20.02-fixes (i think) with Feisty Fawn Ubuntu. I recently tried doing this as well and for some reason I put a cd in the  dvd-writer instead of a dvd (silly me), well the log window starting filling up with info and all looked well but when I looked at it a couple hours later it was still at the same spot (process.log file here: [http://pastebin.com/m30f42ece](http://pastebin.com/m30f42ece)) I tried canceling the process and it says it may take a couple minutes to cancel. I waited for hours (still stayed at same process log screen, so I restarted mythtv, restarted my machine but to no avail, whenever I try to go back to create a different mytharchive dvd, it doesn't give me an option to chose which files to archive, it just goes straight to that same filled in log file screen. I just noticed there are these 2 files within the mytharchive folder: mythburncancel.lck  mythburn.lck, do I need to delete these? Also, here is the mythburn.log file: [http://pastebin.com/m27c3f444](http://pastebin.com/m27c3f444)

Any help would be appreciated.

While it runs, mytharchive puts a lockfile in the tempory directory you designated for mytharchive to work in. The lockfile didn't get deleted because the mytharchive job was terminated and didn't finish its run.

You can delete the lockfile itself, or even nuke the entire temporary directory, since mytharchive rebuilds it from scratch every time it runs.

Cheers! :)

---

### Post by bmwman on 2008-10-04
Here is my version Version: 0.21.0+fixes18207-0ubuntu4~hardy1. If I upgrade to 8.10, is that gonna fix the problem? Or it's going to create more problems?

---

### Post by anonymousdog on 2008-10-04
That is current, but I was wrong on two things in my prior replies:
1. The current version of mythburn.py does NOT include the -use-the-force-luke=notray option.  If you have problems with nothing else but that your drive ejects after writing to media but before the script finishes running, then you'd have to invoke that option for the script not to error out.  In that case you'd have to include -use-the-force-luke=notray in the option set at lines 2602 and 2609 of mythburn.py (unless there's some better way that a developer would know).
2. Your error in post #7 looks like missing mkisofs (not growisofs).  What is the output of 'ls -l `which mkisofs`'?
Out of curiosity (since you originally had problems archiving straight to DVD [with no iso file creation]), what is the output of 'dpkg -S growisofs' (that'll take a while to run).

You have upgraded genisoimage; so, the problem with mytharchive generating DVDs unreadable on Windows boxes should be cured (if that was part of the original issue).

---

