---
title: "How to share DVD files from MythTV back-end to front-end?"
date: 2009-11-27
forum: Mythbuntu
---

### Post by bradsthompson on 2009-11-27
I have all my DVD's backed up on a Ubuntu 9.10 machine running MythTV back-end and Samba.  The files are backed up in the original DVD file structure format (VIDEO_TS .vob structure) and categorized on several different HDDs in that machine.  I've also included .xml files and coverart in the DVD folder for the old MyMovies setup I was running on Windows.
 
What is the best way to get MythTV to find these files automatically and stream them seamlessly to my front-end machine?
 
I will still probably load any new DVD's using a windows laptop over my home network... I just need them working on MythTV now.

---

### Post by bradsthompson on 2009-11-29
bump

---

### Post by jimp180 on 2009-11-29
> **bradsthompson said:**
> I have all my DVD's backed up on a Ubuntu 9.10 machine running MythTV back-end and Samba.  The files are backed up in the original DVD file structure format (VIDEO_TS .vob structure) and categorized on several different HDDs in that machine.  I've also included .xml files and coverart in the DVD folder for the old MyMovies setup I was running on Windows. are these in ISO file format? 
 
> **bradsthompson said:**
> What is the best way to get MythTV to find these files automatically and stream them seamlessly to my front-end machine?if they are in ISO format you can set the "videos" directory settings in the setup to point to the folder they are stored in and then go to "watch videos" on your frontend and they should show up.
 
> **bradsthompson said:**
> I will still probably load any new DVD's using a windows laptop over my home network... I just need them working on MythTV now.why? theres nothing easier than using the built in ripper program to rip your dvds and save them as ISO files in your video directory. just make sure your video directory has read/write permissions.

---

### Post by Boppy3125 on 2009-11-30
First, you need to mount them on the remote front end the same way they are on the other one.  ie /var/lib/mythtv/videos/{movie name} should be the same.  So share out videos on the BE, mount that to that same location on the FE.  (You only need them both at the same location if you will ever watch or scan for new videos on BOTH machines.  MythVideo is setup to store the absolute path in the database, so they have to match if coming from different machines.)

Then you have to configure MythVideo to use this particular folder.  Next time you scan for new videos (go to watch videos menu, hit i I think) it should find these videos.

I am not sure how to get the cover art and such recognized.  Maybe someone else can weigh in on that.

---

### Post by bradsthompson on 2009-12-02
> **Boppy3125 said:**
> First, you need to mount them on the remote front end the same way they are on the other one.  ie /var/lib/mythtv/videos/{movie name} should be the same.  So share out videos on the BE, mount that to that same location on the FE.  (You only need them both at the same location if you will ever watch or scan for new videos on BOTH machines.  MythVideo is setup to store the absolute path in the database, so they have to match if coming from different machines.)

Then you have to configure MythVideo to use this particular folder.  Next time you scan for new videos (go to watch videos menu, hit i I think) it should find these videos.

I am not sure how to get the cover art and such recognized.  Maybe someone else can weigh in on that.

Thank you!  You'll have to forgive me because I'm still brand new to Ubuntu and Linux in general (and am probably biting off way more than I can chew) but how exactly do I mount the files on the Front-end and the Back-end?

Right now, the files are stored on a separate drive on my computer like so:

D:[Media Drive 1]
--DVDs
----My Movies
------[Movie A]
--------VIDEO_TS
--------AUDIO_TS
------[Movie B]
--------VIDEO_TS
--------AUDIO_TS
----My TV Shows
------[TV Series A]
--------[TV Series A - Disc 1]
----------VIDEO_TS
----------AUDIO_TS
------[TV Series B]
--------[TV Series B - Disc 1]
----------VIDEO_TS
----------AUDIO_TS

In this structure, each disc has its own folder with a different name but within that folder exists a folder named VIDEO_TS that contains multiple .vob files.

---

### Post by ahood on 2009-12-02
> **bradsthompson said:**
> ..how exactly do I mount the files on the Front-end and the Back-end?

Right now, the files are stored on a separate drive on my computer like so:

D:[Media Drive 1]
--DVDs
----My Movies
------[Movie A]
--------VIDEO_TS
--------AUDIO_TS
------[Movie B]
--------VIDEO_TS
--------AUDIO_TS
----My TV Shows
------[TV Series A]
--------[TV Series A - Disc 1]
----------VIDEO_TS
----------AUDIO_TS
------[TV Series B]
--------[TV Series B - Disc 1]
----------VIDEO_TS
----------AUDIO_TS

Previous poster was correct. You will need to determine the path that movie files are stored in Ubuntu. The post above is a tad confusing because the first line above, **D:[Media Drive 1]** is not standard Ubuntu/Linux syntax. 

In ubuntu/Linux, the path will begin with a /

It may sound strange, but all files, folders, and even devices are mounted somewhere under /

So, Ubuntu/Linux typically mounts a flash drive in /media and full path will be /media/usbdisk.

People familiar with Ubuntu/Linux may customize where a hard disk will be mounted. For instance, my tv shows and movies are stored on a second internal hard drive and mounted in my home directory or /home/username/mythtv.

If you can give the path beginning with a / to the mount folder of the hard drive storing the video files in Ubuntu, then we may be able to give more detailed instructions.

Cheers,

---

### Post by bradsthompson on 2009-12-03
> **ahood said:**
> Previous poster was correct. You will need to determine the path that movie files are stored in Ubuntu. The post above is a tad confusing because the first line above, **D:[Media Drive 1]** is not standard Ubuntu/Linux syntax. 
 
In ubuntu/Linux, the path will begin with a /
 
It may sound strange, but all files, folders, and even devices are mounted somewhere under /
 
So, Ubuntu/Linux typically mounts a flash drive in /media and full path will be /media/usbdisk.
 
People familiar with Ubuntu/Linux may customize where a hard disk will be mounted. For instance, my tv shows and movies are stored on a second internal hard drive and mounted in my home directory or /home/username/mythtv.
 
If you can give the path beginning with a / to the mount folder of the hard drive storing the video files in Ubuntu, then we may be able to give more detailed instructions.
 
Cheers,
 
 
I guess the path(s) to the VIDEO_TS folder would be /media/media drive 1 with all subfolders following like so:
 
/media/media drive 1/dvds/my movies/movie a/VIDEO_TS

---

### Post by tgm4883 on 2009-12-03
> **bradsthompson said:**
> I guess the path(s) to the VIDEO_TS folder would be /media/media drive 1 with all subfolders following like so:
 
/media/media drive 1/dvds/my movies/movie a/VIDEO_TS

You will need to use NFS or CIFS to mount that directory on your remote frontend so that the movie shows up in the same location (the full path to each must be the same)

---

### Post by Boppy3125 on 2009-12-03
Ubuntu has some GUI tool for helping configure the NFS shares.  I think you can just browse out with the Thunar file manager, right click the folder you want to share, and just start poking around for NFS.  (Or do some google-ing for ubuntu nfs)

Then on the Frontend you want to mount.  I found this page to be helpful when I was setting mine up.

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

The key if you want to be able to watch them on both computers is that the path is identical.  So if "/media/media drive 1/dvds" is a folder on the Backend, you will want to share it with NFS.  Then on the Frontend, you will want to create that same folder, then using the fstab file to mount the Backend's share as that folder.

---

### Post by ahood on 2009-12-06
> **bradsthompson said:**
> I have all my DVD's backed up on a Ubuntu 9.10 machine running MythTV back-end and Samba.  
 
What is the best way to get MythTV to find these files automatically and stream them seamlessly to my front-end machine?

In case you need a how-to on getting this to work. Below are my recommended steps.

**A. Create symlink on Mythtv Backend + Samba running on Ubuntu**
The reason is to make it easier to enter information in parts B and C below.

Open a terminal and enter...

> sudo ln -s /mnt/mythvideos "/media/media drive 1/dvds/my movies/movie a/VIDEO_TS"

*Note: I included quotes (") in the above command because of the spaces in hardlink path.*

The permissions of the symlink (/mnt/mythvideos) will be inherited from the hardlink.

**B. Update mythtv backend + samba machine to use /mnt/mythvideos directory for storage of video recordings.[COLOR="Red"] - IMPORTANT[/COLOR]**

**C. Share folder on Mythtv Backend + Samba running on Ubuntu**
If using regular Ubuntu, use nautilus file manager to find the video folder to share (i.e., /mnt/mythvideos), right-click the folder and click on 'Sharing Options'. Fill with appropriate information.

If using Mythbuntu, exit out of the frontend (if running) and click on Applications --> System --> Share Folders, fill with appropriate info 

*Note: Recommend using a simple share name, like 'mythvideos'*
*Note: Recommend sharing as read-only.*

**D. On mythtv remote frontend, mount shared folder**

Exit out of the frontend
Launch the terminal, Applications --> Accessories --> Terminal
Create local directory to mount
> sudo mkdir /mnt/mythvideos
Edit fstab so that share is mounted locally
> sudo nano /etc/fstab
Add the following line
> //*[COLOR="Blue"]ipaddressmythtvbackend[/COLOR]*/mythvideos /mnt/mythvideos cifs auto,username=*[COLOR="Blue"]username[/COLOR]*,password=*[COLOR="Blue"]userpassword[/COLOR]*,uid=1000,umask=000,user 0 0 

*Note: User name and password are for the user on the Mythtv backend + samba machine.*

On remote mythtv frontend, remount drives and shares specified in fstab
> sudo mount -a
Report any error messages returned.

On remote mythtv frontend, list contents of new local mount.
> ls /mnt/mythvideos
Report if no files or directories are returned.

**E. Update remote mythth frontend**
Start the mythtv frontend on remote machine.
Update the storage directory of the myth videos to /mnt/mythvideos.

I hope this helps.

---

