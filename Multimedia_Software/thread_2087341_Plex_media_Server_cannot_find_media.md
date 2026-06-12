---
title: "Plex media Server cannot find media"
date: 2012-11-23
forum: Multimedia Software
---

### Post by politenessman on 2012-11-23
I'm running Xubuntu (XFCE 4.8 and Ubuntu 11.10)
I've just intalled the Plex media server and I seem to be having some difficulty in getting it to recognize my media files.

My first problem is that my laptop hard drive is fairly small so some of my media sits on an external USB drive. When setting the path for the the media libraries, the USB drive is recognized, but I can only point as far as the drive itself. There is no option to expand and select sub directories. I suspect this is the root of the problem.

If I just write the full path into the path box, the media files are still not recognized.

The same thing happens for media actually in my home directory. I can point to /Home, but no further.

Is this is permissions issue and if so, how do I selve it?

---

### Post by mikegoodman on 2012-12-13
Running Ubuntu 12.10
I have seemingly identical problems with Plex Media Server not finding my media files
Plex works perfectly on my home drive accessing directories and sub directories but will not recognize directories or files on a second internal hard drive (it is mounted).
Again I can read and write files to this second hard drive normally, it is only Plex that does not recognise directories on the drive, it does see the drive.
I too wonder if this is a permissions issue but as I can access the drive when logged in it does seem unlikely.
Plex did work under 12.04 with the second hard drive no problems at all.

I wonder if anyone has any thoughts?

---

### Post by joachim.j on 2012-12-17
Affects me as well in Ubuntu 12.10.

---

### Post by jorny32 on 2012-12-29
I am also having this problem. I have a secondary hard drive with files on it I'd like Plex to read. I thought it had to do with permissions, but I tried different things like chmod and the group command to change permission, even changed the ownership to the Plex user and still can't see it.

Is it that it's a mountable drive?

---

### Post by bman on 2012-12-30
Exact same problem, thought I was doing permissions wrong or something, but it's not me.

Anyone figure this out?

---

### Post by gendolookin on 2013-01-02
I'm not sure you have the same problem as me. 

I had a separate hard drive that stores all my movies and tv shows.  This was a left over drive from an old windows install. 

I could not get Plex to see the media.  

What I realized was, the drive wasn't mounting automatically, and would only mount when i went to access it.  This made me think that maybe that was causing plex a problem. 

I added the second hard drive to my fstab file, and that fixed the problem.

---

### Post by jualin on 2013-01-16
> **gendolookin said:**
> I'm not sure you have the same problem as me. 

I had a separate hard drive that stores all my movies and tv shows.  This was a left over drive from an old windows install. 

I could not get Plex to see the media.  

What I realized was, the drive wasn't mounting automatically, and would only mount when i went to access it.  This made me think that maybe that was causing plex a problem. 

I added the second hard drive to my fstab file, and that fixed the problem.

Hi guys, just ran into this issue today. As others have mentioned in other forums the problem is that the "plex" user doesn't belong to the "plugdev" group which is the only group that has access to the mounted devices. 
All you need to do is to add plex to that group by using gpasswd 
```
sudo gpasswd -a plex plugdev
```
To check that the "plex" user belongs to that group we can issue the following command:
```
groups plex
```

Which should display something like: plex: plex plugdev

Restart your computer and try to access the mounted media with Plex Media Manager. If for some reason that doesn't work then you might need to add plex to your own user group. Some may consider this a bit risky since plex would be able to do almost anything that your user (in my case "jualin") can do.
Either way, we use gpasswd again:
```
sudo gpasswd -a plex yourUser
```

If none of this works then check the permissions of your mounted media using "ls -l". In my case my Windows partition is mounted on /windows/ and the output of "ls -l" shows that the group (the 4th column) that has access is "plugdev"
```
jualin@cari:/$ ls -l
drwxrwx---    1 root plugdev  8192 Jan 14 00:16 windows
jualin@cari:/$ 

```

Hope this helps! :)

---

### Post by Rsxhawk on 2013-01-18
I am having a similiar issue in 12.04 with Plex.  I cannot for the life of me get it to see whats in my movies folder on my storage drive (its mounted).  It see's the drive in /media but beyond that, nothing.  I even tried it in a folder in my home directory as others have tried and it still won't see anything.  I will try messing with the permissions and see if that's the problem.  Very strange.  Does it matter that the storage drive is NTFS?

---

### Post by Rsxhawk on 2013-02-18
So apparently it does matter that my storage drive was NTFS as Linux cannot change permissions on NTFS file systems.  It makes sense, but no one in this thread had that answer, found it in another thread.  I'll chalk that up to my noob-ness when it comes to filesystem knowledge, but hey, I learned something new.

I moved all my data off my NTFS drive, reformatted the drive to EXT4, moved all my data back and chmod all the permissions for my media plus using the above tactic of putting the plex user in the plugdev group (and my user group as well), and voila, Plex can see all my media now.

---

### Post by haider254 on 2013-08-06
[size=1]> **jualin said:**
> hi guys, just ran into this issue today. As others have mentioned in other forums the problem is that the "plex" user doesn't belong to the "plugdev" group which is the only group that has access to the mounted devices. 
All you need to do is to add plex to that group by using gpasswd 
```
sudo gpasswd -a plex plugdev
```
to check that the "plex" user belongs to that group we can issue the following command:
```
groups plex
```

which should display something like: Plex: Plex plugdev

restart your computer and try to access the mounted media with plex media manager. If for some reason that doesn't work then you might need to add plex to your own user group. Some may consider this a bit risky since plex would be able to do almost anything that your user (in my case "jualin") can do.
Either way, we use gpasswd again:
```
sudo gpasswd -a plex youruser
```

if none of this works then check the permissions of your mounted media using "ls -l". In my case my windows partition is mounted on /windows/ and the output of "ls -l" shows that the group (the 4th column) that has access is "plugdev"
```
jualin@cari:/$ ls -l
drwxrwx---    1 root plugdev  8192 jan 14 00:16 windows
jualin@cari:/$ 

```
[/size]
hope this helps! :)

THIS was a huge part in solving this issue! I've been working on this for a good few hours now and this made my day (almost).

Just incase anyone else stumbles upon this and needs help I'll post what I did to make it work.

I implemented the solution above but also changed the mount point for the USB hard drive. I put it in the same location as all my plex media.

Now I'm a linux noob, if I make a mistake please do correct me, but I'll make an attempt to explain how I got mine to work....

First I figured out what my USB device name is (/dev/sd***), I personally did this with gparted and found that the partition I wished to share was /dev/sdc1 (I think this can also be accomplished with:```
 sudo fdisk -l
```

Once I got this infomation I created the mount point directory, now for this I simply used nautilus and created the folder. I also changed group permission to plugdev to coincide with Jualin's advice (for my share I also added plex to sambashare because I wasn't sure if the parent folders ownership would affect the USB device as I mounted it to the sambashare location, I wanted to make sure I can access the USB via samba).

Now it's time to mount the USB drive, follow along:

```
sudo gedit /etc/fstab
```

add the following line (correcting for your *dev*, *dir* and file system (it works with ntfs which surprised me thorougly, also allowing me to read/write from my windows computer)

```
/dev/sdc1 /home/user/videos/usb ntfs defaults 0 0
```

Once I saved the file, I opened up Plex and it worked!

Thanks for the help, and I hope my messy and distorted post will help someone...

edit:

just an quick update. it looks as though you will need to add the usb mount point directory (in my case /home/user/videos/USB) to the plex library, the parent directory didn't suffice in my case. probably a permissions issue, I'm sure with a little bit of messing around you could get it work without this add, but I decided I'm fine with having 2 directories for plex to look in.

---

### Post by TheDavidJohnson on 2013-08-24
Thank you to everyone for the info in this thread. I'm on Ubuntu 12.04 LTS 32-bit and was unable to mount my external USB drive to any location other than /mnt and have Plex recognize it. This thread gave me the tipoff: [http://ubuntuforums.org/showthread.php?t=2139064](http://ubuntuforums.org/showthread.php?t=2139064) 

Ultimately I had to add the plex user to my group as well, but it's working quite nicely now!

---

### Post by drew-j-harrison on 2013-08-30
[COLOR=#000000][FONT=Arial]Appreciate all the tips but I am still having the same problem here. Reformatted from NTFS to EXT4, added permissions for both plugdev and 'drew' groups and still getting zero recognition of folders or files from Plex (FYI XBMC has no problem). Currently using 13.04 with a Mediasonic 8 drive RAID box (HF2-SU3S2) over eSATA[/FONT][/COLOR][COLOR=#000000][FONT=Arial]*. *[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Any help is appreciated already have 10 hours in to this problem to no avail. Here's couple clips from the terminal checks if this helps at all.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]```
drew@Drews-Home-Office-PC:~$ groups plex

```[/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]plex : plex plugdev drew[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]```
drew@Drews-Home-Office-PC:~$ ls -l

```[/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]total 56[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxr-xr-x 2 drew drew 4096 Aug 28 19:05 Desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxr-xr-x 2 drew drew 4096 Aug 30  2009 Documents[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxr-xr-x 3 drew drew 4096 Aug 30 02:20 Downloads[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]-rw-r--r-- 1 drew drew 8445 Aug 30  2009 examples.desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxrwxr-x 5 drew drew 4096 Jan 24  2013 FrostWire[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxr-xr-x 2 drew drew 4096 Aug 29 20:46 Music[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxr-xr-x 2 drew drew 4096 Aug 30  2009 Pictures[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]lrwxrwxrwx 1 drew drew   36 Jan 23  2013 PlayOnLinux's virtual drives -> /home/drew/.PlayOnLinux//wineprefix/[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]drwxr-xr-x 2 drew drew 4096 Aug 30  2009 Public[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxr-xr-x 2 drew drew 4096 Aug 30  2009 Templates[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxrwxr-x 2 drew drew 4096 Jan 22  2013 Ubuntu One[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxr-xr-x 2 drew drew 4096 Aug 30  2009 Videos[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]drwxrwxr-x 2 drew drew 4096 Jan 23  2013 Windows Apps[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]The current file path for the storage is /media/drew/Media Storage[/FONT][/COLOR]

---

### Post by drew-j-harrison on 2013-08-30
I got it working just had to change the mount location.  As posted in another thread apparently it is not possible for anything other than the system to access the default mounting location.

---

### Post by TimEnid on 2013-08-31
Can someone walk me thru this? I am having the same issue. The drives marked Movies and Home are the ones i want to show up in plex.
> tim@tim:/media/tim$ ls -l
total 484
drwx------ 2 root root      4096 Aug 16 22:18 Buffalo 1.5tb
drwx------ 1 tim  tim      28672 Aug 31 01:33 Buffalo 1.5tb1
drwx------ 2 root root      4096 May  6 16:52 Buffalo 3.0
drwx------ 2 root root      4096 Aug 16 22:18 Buffalo 3.01
drwx------ 1 tim  tim     430080 Aug 31 11:00 Buffalo 3.02
drwxrwxr-x 1 tim  tim       8192 May 26 16:54 Home
drwx------ 2 root root      4096 May 31 19:49 Iomega 3.0
drwxrwxrwx 2 tim  tim       4096 Apr 27 13:04 Media
drwxrwxrwx 5 tim  plugdev   4096 Aug 31 12:12 Movies
drwxrwxrwx 1 root root      4096 May 25 19:55 WD

---

### Post by drew-j-harrison on 2013-09-05
> **TimEnid said:**
> Can someone walk me thru this? I am having the same issue. The drives marked Movies and Home are the ones i want to show up in plex.

I actually did not use the terminal to mount it.  Under the disk manager you can select the partition settings and modify the mount options.  It's fairly straight forward.  If you are still having issues reply again and I will try and give further detail.  FYI NTFS works just fine.

---

### Post by moyeboy13 on 2014-01-03
all, i'm still having a problem with my Plex install on 13.04.  i have done much (if not all) of what has been suggested here.  i have moved the mount point of my Pictures volume to /mnt/Pictures from /media/Pictures.  i have added the plex user to the plugdev group as well as my username group.  Plex still cannot find the media located in that directory.

a little about my system.  it's an older machine, hence why i want to run Plex on Ubuntu instead of Windows.  i took a single 2TB drive and formatted it into an extended partition (ext4) and created multiple partitions.  the reason i wanted to do it this way is so that my girls could see their shows in their libraries instead of seeing mom & dad's movies/tv shows or music files.

i'm really at a loss at this point.  i did a chmod 777 on the /mnt/Pictures partition and it's owner is my username.  what am i missing?

thanks for any assistance that you might be able to provide.

---

### Post by TimEnid on 2014-01-03
> **moyeboy13 said:**
> all, i'm still having a problem with my Plex install on 13.04.  i have done much (if not all) of what has been suggested here.  i have moved the mount point of my Pictures volume to /mnt/Pictures from /media/Pictures.  i have added the plex user to the plugdev group as well as my username group.  Plex still cannot find the media located in that directory.

a little about my system.  it's an older machine, hence why i want to run Plex on Ubuntu instead of Windows.  i took a single 2TB drive and formatted it into an extended partition (ext4) and created multiple partitions.  the reason i wanted to do it this way is so that my girls could see their shows in their libraries instead of seeing mom & dad's movies/tv shows or music files.

i'm really at a loss at this point.  i did a chmod 777 on the /mnt/Pictures partition and it's owner is my username.  what am i missing?

thanks for any assistance that you might be able to provide.
i changed my mount point to /srv/movies and plex fines it just fine.

---

### Post by jsavga on 2014-02-11
> **jualin said:**
> Hi guys, just ran into this issue today. As others have mentioned in other forums the problem is that the "plex" user doesn't belong to the "plugdev" group which is the only group that has access to the mounted devices. 
All you need to do is to add plex to that group by using gpasswd 
```
sudo gpasswd -a plex plugdev
```
To check that the "plex" user belongs to that group we can issue the following command:
```
groups plex
```

Which should display something like: plex: plex plugdev

Restart your computer and try to access the mounted media with Plex Media Manager. 

Thank you so much for that. Running 13.10, I added plex to the plugdev group, rebooted and now it sees my media. I can now click on my mounted Windows drives and get the directories list (before it wouldn't show anything other than the drive) and select the media directories and they show up in plex. Thanks again.

---

### Post by midimarcus on 2014-03-01
I had same problem on Ubuntu 13.10 with a second HD, in my case auto-mounted at boot, and I solved it by changing permissions of mounted folder.
My mountpoint was /media/moovee with "movies" and "tvshows" folder inside.
Initial permissions were:
```
drwx------ moovee 700
```

and plex was unable to scan files in subfolders.
When I set 777 permissions:
```
drwxrwxrwx moovee
```

In my case 777 can be safe enough, but consider setting more restrictive permissions depending on your specific needs (personal or shared pc, nas, etc...).

Hope this help.

---

### Post by Ivan_C on 2014-04-28
> **drew-j-harrison said:**
> I actually did not use the terminal to mount it.  Under the disk manager you can select the partition settings and modify the mount options.  It's fairly straight forward.  If you are still having issues reply again and I will try and give further detail.  FYI NTFS works just fine.

Could someone else confirm NTFS works?  I have a 1TB HDD which was originally running windows 7 so the whole thing is running on NTFS.  I decided to dual boot Linux Mint based on Ubuntu by making some space for the OS partition.  The dual boot thing works fine but I want to have plex media server running as this is intended to be a headless media server.

Plex can only see my root directory and my home directory, it cannot see the other NTFS partition where I have my media files! .. I tried adding plex to plugdev as advised here but that didn't work.  I still have to try adding plex to my user group but if thats not going to do much I was thinking of buying another hard drive, format it with a filesystem that would play nice with PMS and see if that works.. 

Input anyone? :confused:

---

### Post by stevenrobertlane on 2014-06-15
Most of the methods posted above will work but I have found the easiest way is to change Plex Media Server user to your own user account instead of the plex account.

Type this command to edit the plex script.
sudo nano /etc/default/plexmediaserver

Replace the "plex" user account with your own account.

PLEX_MEDIA_SERVER_USER=plex
Change to
PLEX_MEDIA_SERVER_USER=your user name

control+O to save

Run once
http:// localhost:32400/web/index.html#!/dashboard

Stop:
sudo service plexmediaserver stop

add user to group:
sudo addgroup plex youruser
sudo addgroup youruser plex

start:
sudo service plexmediaserver start

I have messed around with all the other methods and they have worked e.g. mounting partition in different folders and changing permissions but find this method above far easier.

And NTFS is fine.

Hope this helps

---

### Post by John_P_Fusco on 2014-09-01
> **stevenrobertlane said:**
> [SIZE=3][FONT=arial]Most of the methods posted above will work but I have found the easiest way is to change Plex Media Server user to your own user account instead of the plex account.

[COLOR=#333333]Type this command to edit the plex script.[/COLOR]
sudo nano /etc/default/plexmediaserver

Replace the "plex" user account with your own account.

PLEX_MEDIA_SERVER_USER=plex
Change to
PLEX_MEDIA_SERVER_USER=your user name

control+O to save

[COLOR=#333333]Run once[/COLOR]
http:// localhost:32400/web/index.html#!/dashboard

[COLOR=#333333]Stop:[/COLOR]
sudo service plexmediaserver stop
[COLOR=#333333]
add user to group:[/COLOR]
sudo addgroup plex youruser
[COLOR=#333333]sudo addgroup youruser plex[/COLOR]
[COLOR=#333333]
start:[/COLOR]
sudo service plexmediaserver start

I have messed around with all the other methods and they have worked e.g. mounting partition in different folders and changing permissions but find this method above far easier.

And NTFS is fine.

Hope this helps[/FONT][/SIZE]

I created an account to thank you for this solution, worked for me!  FYI for others I am using an NTFS drive.

---

### Post by Innicas on 2014-09-01
Brilliant - thanks stevenrobertlane!
I tried all the previous suggestions and your solution finally got it working for me

---

### Post by kimbirkkjaerlund on 2014-11-19
stevenrobertlane - Thank you so much. It would be nice if your post was on page one instead of the last page. Stupid me tried all the other fixes in vain first.

---

### Post by pat_oleary on 2014-11-22
> **stevenrobertlane said:**
> [SIZE=3][FONT=arial]Most of the methods posted above will work but I have found the easiest way is to change Plex Media Server user to your own user account instead of the plex account......
,...

And NTFS is fine.

Hope this helps[/FONT][/SIZE]
Thank you so much! This was driving me nuts. Have a 1TB a USB drive from old XP system, NTFS formatted with lots of movies, TV and music, and Plex just refused to see any files, or change permissions (well that's Ubuntu, not Plex). 

But your solution works perfectly.
Thank you for your generosity in typing in clear, comprehensive instructions.

---

### Post by davekerr-x on 2015-03-10
I also created an account just to thank stevenrobertlane for the solution. Thanks!

---

### Post by kungfu-monkey on 2015-03-30
> **stevenrobertlane said:**
> [SIZE=3][FONT=arial]Most of the methods posted above will work but I have found the easiest way is to change Plex Media Server user to your own user account instead of the plex account.

[COLOR=#333333]Type this command to edit the plex script.[/COLOR]
sudo nano /etc/default/plexmediaserver

Replace the "plex" user account with your own account.

PLEX_MEDIA_SERVER_USER=plex
Change to
PLEX_MEDIA_SERVER_USER=your user name

control+O to save

[COLOR=#333333]Run once[/COLOR]
http:// localhost:32400/web/index.html#!/dashboard

[COLOR=#333333]Stop:[/COLOR]
sudo service plexmediaserver stop
[COLOR=#333333]
add user to group:[/COLOR]
sudo addgroup plex youruser
[COLOR=#333333]sudo addgroup youruser plex[/COLOR]
[COLOR=#333333]
start:[/COLOR]
sudo service plexmediaserver start

I have messed around with all the other methods and they have worked e.g. mounting partition in different folders and changing permissions but find this method above far easier.

And NTFS is fine.

Hope this helps[/FONT][/SIZE]

THANK YOU!!!!  I was banging my head trying to get this to work, none of the previous suggestions did anything.  Now I need to sit down and undo the permissions mods I made to the PLEX account.  Genius idea to switch plex to use my account, worked like a charm.  Thanks again!

---

### Post by LowSky on 2015-07-06
I know this tread is old but thank you stevenrobertlane!

I have no idea why my music wasn't adding to Plex, but this solved the problem.

---

### Post by Finston on 2015-08-10
I again joined this thread late. I stream from the Plex Media Server to the TV using a Roku1 box and the free RARflix app, which doesn't get much publicity. However, I could not get music files to be recognised when creating a music library. 

I found that the instructions of stevenrobertlane worked well, however all my previous Plex settings were lost. The Plex Media Server was now open on my machine.

Undaunted, I opened the PlexTVweb based app [https://app.plex.tv/web/app](https://app.plex.tv/web/app) and linked the two from the web app (The original linking was by now lost). All setings were left on default (the web app allows you to change Agents and order of option usage - typically not well explained on Plex)

I then thought that I would do best by setting my music files to a tree format in file manager (the default one looking like a filing cabinet). I selected Files Preferences/List View/Navigate folders in a tree (box ticked). I left the file manager open.

I found that the music files could then be uploaded, when creating a new music librar, by using the plex music manager (I can't remember its name) rather than the itunes music manager (even though my files were ranked as per i-tunes). The tip here was to go to home/username/music and then highlight all the actual music files in the music folder (left click and draw the cursor down the l.h.s. of the file names - blue highlight).

All my video files uploaded as well as ever and I spent some time re-installing all the interesting sounding channels.
 
I hope that this is useful to others. I was stumped. Plex is a great system, but not well explained. Even now I suspect that it can stream live content from my laptop screen - Musictube for example - but that will be a different thread.

---

### Post by chris262 on 2016-01-01
> **stevenrobertlane said:**
> Most of the methods posted above will work but I have found the easiest way is to change Plex Media Server user to your own user account instead of the plex account.

Type this command to edit the plex script.
sudo nano /etc/default/plexmediaserver

Replace the "plex" user account with your own account.

PLEX_MEDIA_SERVER_USER=plex
Change to
PLEX_MEDIA_SERVER_USER=your user name

control+O to save

Run once
http:// localhost:32400/web/index.html#!/dashboard

Stop:
sudo service plexmediaserver stop

add user to group:
sudo addgroup plex youruser
sudo addgroup youruser plex

start:
sudo service plexmediaserver start

I have messed around with all the other methods and they have worked e.g. mounting partition in different folders and changing permissions but find this method above far easier.

And NTFS is fine.

Hope this helps

Many thanks [**[COLOR=#000000]stevenrobertlane[/COLOR]**]("http://ubuntuforums.org/member.php?u=1929627"). Your solution worked a charm. Thank you to everyone else who also contributed.

---

### Post by Peter_Bannon on 2016-01-18
> **jualin said:**
> Hi guys, just ran into this issue today. As others have mentioned in other forums the problem is that the "plex" user doesn't belong to the "plugdev" group which is the only group that has access to the mounted devices. 
All you need to do is to add plex to that group by using gpasswd 
```
sudo gpasswd -a plex plugdev
```
To check that the "plex" user belongs to that group we can issue the following command:
```
groups plex
```

Which should display something like: plex: plex plugdev

Restart your computer and try to access the mounted media with Plex Media Manager. If for some reason that doesn't work then you might need to add plex to your own user group. Some may consider this a bit risky since plex would be able to do almost anything that your user (in my case "jualin") can do.
Either way, we use gpasswd again:
```
sudo gpasswd -a plex yourUser
```

If none of this works then check the permissions of your mounted media using "ls -l". In my case my Windows partition is mounted on /windows/ and the output of "ls -l" shows that the group (the 4th column) that has access is "plugdev"
```
jualin@cari:/$ ls -l
drwxrwx---    1 root plugdev  8192 Jan 14 00:16 windows
jualin@cari:/$ 

```

Hope this helps! :)


I can verify that adding the plex user to the plugdev group worked for me.  Running the media server on a laptop and it was only picking up 2 albums out of about 70 which were newly downloaded albums.  After modifying the user groups its now recognising all the files.

They could do with updating the verbose information to reflect permission based issues rather than just "removing parent from the mapping"

---

### Post by applepiefrost on 2016-08-10
> **stevenrobertlane said:**
> Most of the methods posted above will work but I have found the easiest way is to change Plex Media Server user to your own user account instead of the plex account.

Type this command to edit the plex script.
sudo nano /etc/default/plexmediaserver

Replace the "plex" user account with your own account.

PLEX_MEDIA_SERVER_USER=plex
Change to
PLEX_MEDIA_SERVER_USER=your user name

control+O to save

Run once
[http://localhost:32400/web/index.html#!/dashboard](http://localhost:32400/web/index.html#!/dashboard)

Stop:
sudo service plexmediaserver stop

add user to group:
sudo addgroup plex youruser
sudo addgroup youruser plex

start:
sudo service plexmediaserver start

I have messed around with all the other methods and they have worked e.g. mounting partition in different folders and changing permissions but find this method above far easier.

And NTFS is fine.

Hope this helps

Did something change with Plex causing this to no longer work? 

I'm using Ubuntu 16.04.1 LTS and Plex Media Server 2.7.4

The problems I'm having are these:

The file plexmediaserver doesn't seem to exist in /etc/default

```
stark@FRIDAY:/etc/default$ ls -l | grep plex
-rw-r--r-- 1 root root  832 Aug 10 19:18 plexmediaserver.prev
```

plexmediaserver.prev exists and contains the same info (I assume) as "plexmediaserver" would have contained. I changed the username in that file from "plex" to "stark". 

However, when the Plex Media Server is run, it's still being run as "plex" and not "stark".

```
stark@FRIDAY:/etc/default$ ps aux | grep plex
plex     31272  0.0  0.0   4508   836 ?        Ss   19:31   0:00 /bin/sh -c LD_LIBRARY_PATH=/usr/lib/plexmediaserver /usr/lib/plexmediaserver/Plex\ Media\ Server
plex     31274 15.4  1.3 520804 111656 ?       Sl   19:31   0:01 /usr/lib/plexmediaserver/Plex Media Server


```

When I try to add a portable drive to my library, I only see the root of the drive and not any of the underlying folders. 


Has anyone else tried this recently and knows what to do? Any help is appreciated.

---

### Post by applepiefrost on 2016-08-10
So a little follow up to myself. I stumbled across this thread: [https://ubuntuforums.org/showthread.php?t=2139064](https://ubuntuforums.org/showthread.php?t=2139064) where user [**[COLOR=#000000]dcstar[/COLOR]**]("https://ubuntuforums.org/member.php?u=7532") says
> 
/media is a System Folder for exclusive use by the System to mount and unmount removable devices. It should **not** be used for anything that requires a fixed mount point.

If you want fixed locations, create a mount point in /mnt and edit your /etc/fstab files to use it. 				

So I changed the mounting location away from /media and now all of a sudden my files are appearing in Plex Media Server. I don't know if it's the same answer for everyone, but that's what fixed it for me.

---

### Post by ajgreeny on 2016-08-10
> **applepiefrost said:**
> So a little follow up to myself. I stumbled across this thread: [https://ubuntuforums.org/showthread.php?t=2139064](https://ubuntuforums.org/showthread.php?t=2139064) where user [**[COLOR=#000000]dcstar[/COLOR]**]("https://ubuntuforums.org/member.php?u=7532") says


So I changed the mounting location away from /media and now all of a sudden my files are appearing in Plex Media Server. I don't know if it's the same answer for everyone, but that's what fixed it for me.
I have had success in a similar way.

If visitors bring USBs with photos/videos which I wish to show using PMS on my TV using a smart-set-top-box with a side-loaded plex client, I have added an alias for usb which unmounts the usb after insertion them mounts it to a folder in my home created specifically for the purpose.  ```
alias usb='sudo umount /dev/sdf1 && sudo mount /dev/sdf1 /home/$USER/Plex-client/'
```sdf1 is the device name for all usb disks when inserted (unless it's a second inserted disk when it will be sdg1).

Following that, and after a quick rescan of that library in the plex webindex page in a browser, the pics or videos all show fine using plex.

---

### Post by colin.p on 2017-01-26
> **applepiefrost said:**
> So a little follow up to myself. I stumbled across this thread: [https://ubuntuforums.org/showthread.php?t=2139064](https://ubuntuforums.org/showthread.php?t=2139064) where user [**[COLOR=#000000]dcstar[/COLOR]**]("https://ubuntuforums.org/member.php?u=7532") says


So I changed the mounting location away from /media and now all of a sudden my files are appearing in Plex Media Server. I don't know if it's the same answer for everyone, but that's what fixed it for me.

Well after an afternoon with at least a dozen tabs open in Chrome and several reboots and the odd curse word, I can now say that my external NTFS drive now allows media to show up in Plex. This last issue with the mount point of said drive was the clincher. If it breaks again - I fix it with the 8lb maul.

---

