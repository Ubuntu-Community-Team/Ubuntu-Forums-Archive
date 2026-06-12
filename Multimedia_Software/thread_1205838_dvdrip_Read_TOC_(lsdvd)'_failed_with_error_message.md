---
title: "dvd::rip Read TOC (lsdvd)' failed with error message"
date: 2009-07-06
forum: Multimedia Software
---

### Post by lotster on 2009-07-06
Hi!

I installed DVD::RIP and successfully converted one movie to AVI.  However, now I'm trying it with another disc, when I click on "Read DVD table of contents" it says:

> Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.

I Googled for a solution, and found other people with similar problems, but couldn't find a solution anywhere.

For the record, I have only one DVD drive, so I don't have the wrong one selected; and obviously I have the disc inserted (I have re-inserted it many times).

Can anyone please help me?

---

### Post by lotster on 2009-07-07
All right; I found a solution, sort-of.  I'm just posting it here in case someone else stumbles onto this post.

All I did was to rip the DVD using DVD Shrink on my Windows PC (I know you can get DVD Shrink to work in WINE as well, though I've never done it), then I transferred the files to my Ubuntu PC and loaded the folder into dvd::rip as a "disc image directory".  Worked 100%.

I hope this helps someone...

---

### Post by icewalkers on 2009-08-27
It works better if you enter the mount point of your DVD player usually [/media/cdrom/] under standard Ubuntu release.

---

### Post by hurt138 on 2009-11-15
You need to install libdvdcss2, which you can find doing a google search for "libdvdcss2 deb".

---

### Post by Jasev on 2010-01-04
I am having the same problem with dvd::rip but I already have libdvdcss2 installed (from the Ubuntu 9.10 repository). I tried reinstalling it but no luck. This issue seems to be in quite a few forums, but as a previous person noted, there is no solution to any of the threads. 

Someone suggested on one thread I read (can't find it again now) that it could be an issue with SATA dvd drives. Does this make sense to anyone? I can play dvd's in vlc, mplayer etc without any problems. I'm running Ubuntu on the latest Mac Book Pro with a 'super slot drive' - I think this is SATA.

Has anyone found other solutions? My ubuntu system and dvd::rip (from the repositories) is up to date as of today.

Thanks!

---

### Post by Jasev on 2010-04-20
For those of you still getting the error message:
"Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive. "
when reading DVD's.

I managed to fix this by accident. I was cleaning up my program list and uninstalled dvdrip-queue. Suddenly I could rip DVD's again. Don't ask me why, but I'm just happy to not to be running dvd-shrink through wine.

Hopefully this also work for some of you.

Cheers

Jason

---

### Post by RaySeys on 2010-04-24
You may need to unmount your dvd first and then re-read the TOC

1. umount /dev/sr0 or whatever your device is
2. in dvd::rip click on 'Read DVD Table of contents' button

---

### Post by breckenr on 2010-12-13
I had this same error with dvdrip after upgrading to Maverick using the Alternate CD as a mounted ISO using the instructions here: [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades).

I realised after looking at the posts here that both the cdrom and cdrom0 links were still present in /media.

After deleting /media/cdrom dvdrip starting working again nicely.

---

### Post by Maximus_ARNP on 2012-12-13
[COLOR="Lime"][SIZE="3"][COLOR="Green"]This is how I fixed it:[/COLOR][/SIZE][/COLOR]
First find out where your movie DVD is mounted. On my computer, it is mounted on:
**[COLOR="Blue"]/media/Name_Of_The_Movie[/COLOR]**
[COLOR="Blue"][B]
Name_Of_The_Movie[/B][/COLOR] will change with each DVD you are trying to rip.

DVD::RIP ---> Edit ---> Edit Preferences:
Change "Default DVD device" to: **[COLOR="Blue"]/media/Name_Of_The_Movie[/COLOR]**

Change "Default data base directory" to:
[B][COLOR="Blue"]/home/username/dvdrip-data[/COLOR]
[/B]
Change "Default directory for .rip project files" to:
[B][COLOR="Blue"]/home/username/dvdrip-data
[/COLOR][/B]
Hit "**[COLOR="Blue"]Check all Settings[/COLOR]**" to confirm that everything is fine.
Hit OK.
Go have **[COLOR="Blue"]fun[/COLOR]** ripping.:popcorn:

---

### Post by oldos2er on 2012-12-13
Old thread closed.

---

