---
title: "Mytharchive Problems"
date: 2008-01-15
forum: Mythbuntu
---

### Post by browndog289 on 2008-01-15
Hello.

I'm having a problem with mytharchive.
To test it I inserted a new blank DVD+RW and got it to archive a movie I recorded. The whole thing was going fine until it got to the end and wanted to eject the disc - I got an I/O error and it terminated. I manually ejected the disc and it worked on my PC without a problem.

I decided to try it again (thinking it would format the disc before writing) but there was a different problem with it:

[FONT="Courier New"]ERROR: Retrying to start growisofs after reload.

--------------------------------------------------------------------------------
ERROR: Failed while running growisofs
Result 36864, Command was: growisofs -Z /dev/dvd -dvd-video -v 'MythTV BurnDVD' /media/mythdisk/mytharchive/temp/work/dvd

Please check the troubleshooting section of the README for ways to fix this error.
--------------------------------------------------------------------------------
Terminated[/FONT]

So then I erased the disc on my PC using Nero and deleted all the temp folders in Mytharchive, but I got the same error.

I tried to manually run the exact command above that it failed on and it said:

[[FONT="Courier New"]genisoimage 1.16 (Linux)
genisoimage: No such file or directory.
Invalid node - 'MythTV BurnDVD'.
:-( Write failed: Input/Output Error.[/FONT]

If I run the same command but omit the 'MythTV BurnDVD' bit then it works fine and records the disc without problems.

How can I fix this in mytharchive?

Thanks for any help you can offer.

browndog

---

### Post by ubnewbie2 on 2008-01-15
I have had a couple of problems with the mytharchive script.  I noticed, somewhere, an opinion that sometimes you have to stop mythtv, and maybe unbuntu, from trying to detect when a new disc is inserted, and take some automatic action.  If it does this, you might get a conflict when the script tries to use the blank DVD to burn the recording.

---

### Post by browndog289 on 2008-01-16
I managed to solve the problem - I had to edit mythburn.py to force it to overwrite a DVD+RW disc as the default behaviour in a script is to fail if the disc contains data. I simply added the [strange] command -use-the-force-luke to the command for growisofs which forces it to record.

However now I have the following error after recording:

Line 3642 in <Module> processJob (job)
Line 3482 in ProcessJob BurnDVDISO()
Line 1536 in BurnDVDISO r=ioctl(f,CDROMEJECT,0)
IOError: [Errno 5] Input/Output Error

This is caused by the system locking the drive so the script cannot eject it. I have turned off disc detection in Mythfrontend, but do I need to configure something else in the system?

browndog

---

### Post by ubnewbie2 on 2008-01-16
This is from the mytharchive section of the mythtv wiki...

```
MythArchive fails to burn the DVD with the error "IOError: [Errno 5] Input/output error"

This error and fix applies to latest svn from trunk only

The exact error looks something like this

 Traceback (most recent call last):
 File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 4681, in main
   processJob(job)
 File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 4483, in processJob
   BurnDVDISO()
 File "/usr/share/mythtv/mytharchive/scripts/mythburn.py", line 2204, in BurnDVDISO
   r = ioctl(f,CDROM.CDROMEJECT, 0)
 IOError: [Errno 5] Input/output error


This is caused by the media monitor mounting and locking the DVD. 
The fix until a better way can be found is to tell the media monitor 
not to monitor the drive you use to burn DVD's. You simply add it to 
the list of devices to ignore on the fourth page of general settings. 
Just unchecking the option to monitor devices doesn't seem to work. 
```

---

### Post by browndog289 on 2008-01-17
I couldn't find the option to add it to ignore, I could only find the CD/DVD drive monitor and it was already disabled.

I have edited mytharchive.py and commented out the lines which eject the disc and the problem is now solved. I just have to eject the disc manually.

---

