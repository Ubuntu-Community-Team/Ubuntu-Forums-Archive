---
title: "What partition for Games. music and stuff on Linux?"
date: 2008-07-13
forum: Multimedia Software
---

### Post by ZpiX on 2008-07-13
Hey

i wondering which partition is the most recommon for Linux when u need to have Games and stuff on it?

---

### Post by UncertainGod on 2008-07-13
Do you mean filesystem?

---

### Post by ZpiX on 2008-07-13
Yeah i think so.. :P im abit noob here :)

---

### Post by bobpaul on 2008-07-13
For some context, this came from a thread about using Valve's Steam games with Wine. Here's the [original post](http://ubuntuforums.org/showpost.php?p=5371243&postcount=15), I asked ZPix to start a new thread.

ZPix, it is important to note the difference between a partition and a filesystem, as UncertainGod pointed out. A partition is a division of the HD into various storage containers. A filesystem is the format through which files and data are stored. Examples of filesystems include NTFS, ext3, reiserfs, FAT (12/16/24/32, etc) and many others.

So your question really has 2 answers, one pertaining to filesystem types and the pros and cons of each, and another relating to the partitioning schemes and why one might want to divide up their HD into multiple containers. Additionally, it could be you're asking the wrong question and the answer you seek is really related more to "How are files and programs organized on *nix. It doesn't look anything at all like my C:\ drive on Windows!"

Some simple answers--Most linux distributions currently use the Ext3 filesystem as their default file system. Wikipedia has [some good information about Ext3](http://en.wikipedia.org/wiki/Ext3), but it's really just Ext2 with journalling added. Journalling prevents against filesystem corruption (though not necessarily data loss) and is the reason you don't see "Check Disk" or anything about "lost clusters" anymore when Windows crashes. NTFS is a journalled filesystem, whereas Fat32--which Win9x and Dos used--is not. Ext3 is the preferred system most of the time simply because it is well tried and tested. While systems like ReiserFS and XFS might provide better performance in certain situations, there are more tools available for repair and data recovery that are capable of working with Ext2/3 than these other systems. Additionally, Ext3 can be tweaked in the mount options to provide similar performance most of the time. For a home user, Ext3 is probably your best choice.

Hmm, that was maybe a bit long ;) Ok. As far as best for "for games, movies, music, pictures and all that?" (from your post in the steam thread)... With respect to filesystems we generally speak in terms of "many large files", "many small files", "mixed data types" etc. The actual type of data isn't important, but the size, frequency of access, and frequency and amount of data change is. As I already said, Ext3 should suite your purposes, at least for the time being.

But since you asked in the steam thread, this part seems best answered with regards to partition scheme and location of data. If you install linux programs and games on linux, they will go somewhere into the main filesystem (/bin, /opt, /usr, etc). When you install things with wine they go into wine's virtual c-drive, which is stored in .wine/drive_c. So, for example, if you install steam, you'll find all programs and data for it are stored in ~/.wine/drive_c/Program\ Files/STEAM/ etc. (You'll note the path uses "/" to separate folders, whereas windows used "\". The "\" here is used to 'escape' the space, so the system knows "Yes, space is part of the filename" and not "Files/STEAM/ is another parameter".) 

Back to linux programs, if you install programs manually--as opposed to through the "Add/Remove Programs", "synaptec", or "apt-get" utilities, they will generally go into /opt or /usr/local. User data *always* defaults into your home folder. This includes documents, pictures, moves, etc that you are working on as well as settings for applications. This is because of file system rights. As a user, you can't write files to anything outside '/home/username' without elevating your privileges temporarily.

Now, you've no doubt noticed Linux doesn't use drive letters (c:, d:, etc) like Windows. Everything is based off of the root folder /. If you want to access something else, like a CD-Rom, an empty folder is created (ex /media/cdrom) and the partition is "mounted" to this location. Mounting just means the contents of the CD are accessible in this location. /media/NAME is the default location, but file systems can be mounted anywhere, which lets you smartly divide your system up into partitions. Whenever I install Linux, I like to keep a separate partition for / and for /home. If I should ever screw things up so badly that I need to reformat and reinstall, I simply tell the install program to "format / and use /dev/sda3 as '/home' but DO NOT format it". When I log back in, things are almost exactly as I left them. If your running a server, there are good arguments for dividing off other folders, but on a desktop machine /home is the most sensible thing to keep on it's own partition if you're going to bother with more than one at all. Knowing where your programs are go to be located (previous paragraph) will help you determine how big the / partition should be and how big the /home partition should be. Most linux applications are relatively small, so I don't usually devote more than 20-30GB for / and then give the rest to /home or divide the test between /home and Windows related stuff. Games tend to be big, though, and linux games will fill / pretty quickly (Quake, UnrealTournament, and a few other major titles have linux versions.) Most major title games, though, are Windows based and would be installed with Wine, so they'd end up in your /home partition--ie, /home/username/.wine/... You can adjust the sizes after the fact, of course, but it's somewhat time consuming and nobody likes leaving their computer relatively unusable for 3 hours when they could be playing Team Fortress 2 :D

Finally, your answer might be best answered with regard to how you use the data. If you still have Windows installed, you might want to access your movies, pictures, etc from both Windows and Linux. Since Linux can access NTFS for both read and write now, having a partition formatted NTFS for these files might be sensible as you'll be able to access them in both windows and linux without extra screwing around. Other options include finding Ext3 filesystem drivers for windows to allow it to access your Ext3 partitions and using FAT32, which would provide better performance on the Linux end but increases your chances of corruption, as it's not journalled.

I suspect I answered more than you originally intended, but I hope I didn't overwhelm you. Welcome to the world of Ubuntu, may your stay be long and pleasant. ;)

---

### Post by ZpiX on 2008-07-13
That was a long speak :)

but helped me alot..

but that i want is i got 2hdd's 1 60GB ATA that i wanna use as filesystem and a 120GB SATA that i got Games and stuff on..

But acttruely my only problem has been steam.. WoW and Diablo is installed on my Sata and running in windowmode whit out any problems both...

or i also got a few other problems whit some drivers to my sound but that not that big deal..

And i dont use Windows anymore.. i changed to Linux becaused i promissed myself to never use Vista :) i just got something whit Microsofts new products XD

---

### Post by bobpaul on 2008-07-13
> **ZpiX said:**
> That was a long speak :)

but helped me alot..

but that i want is i got 2hdd's 1 60GB ATA that i wanna use as filesystem and a 120GB SATA that i got Games and stuff on..

Ok, so the 60GB is where you have Ubuntu installed? Is Ubuntu the only thing on the HD? And I assume the 120GB is currently your NTFS drive and is something you used to use with Windows?

> **ZpiX said:**
> 
But acttruely my only problem has been steam.. WoW and Diablo is installed on my Sata and running in windowmode whit out any problems both...

I'm not quite sure what you mean by "windowmode".

[...snip...]

> **ZpiX said:**
> 
And i dont use Windows anymore.. i changed to Linux becaused i promissed myself to never use Vista :) i just got something whit Microsofts new products XD

In this case, I would recommend reformatting that 120GB to a filesystem Linux can use natively, such as Ext3. While Linux can use NTFS, it requires a lot of CPU overhead. The program "Gparted" (or qtparted if you're on Kubuntu) should help you. You can shrink your NTFS partition, insert an Ext3 partition, move files to the Ext3 partition, and then shrink the NTFS some more until it's empty and you can delete it. Gparted shows up on the in "System -> Administration -> Partition Editor". You can install it with "Add/Remove Programs" or reboot to the LiveCD where it's already installed.

---

### Post by ZpiX on 2008-07-13
> **bobpaul said:**
> Ok, so the 60GB is where you have Ubuntu installed? Is Ubuntu the only thing on the HD? And I assume the 120GB is currently your NTFS drive and is something you used to use with Windows?

Yep


> **bobpaul said:**
> 
I'm not quite sure what you mean by "windowmode".

[...snip...]

Its when u run the game in a Window :)

Hmm now i reformatted my 120GB to ext3.. but now i got a little problem :)

i transfer some Movies and files from my terabyte USB HDD (Fat32 filesystem)

but i dont got the rights to use the files :/ i have to go i terminal and use "sudo Nautilus" and use em/change owner that way :( but cant just use the button that set the same rights for all "under-files" so its kinda annoying and i was also wondering why it dose that? :S

---

### Post by bobpaul on 2008-07-13
> **ZpiX said:**
> Yep
but i dont got the rights to use the files :/ i have to go i terminal and use "sudo Nautilus" and use em/change owner that way :( but cant just use the button that set the same rights for all "under-files" so its kinda annoying and i was also wondering why it dose that? :S

Is this for media on the USB drive directly, or only for stuff you've copied to the ext3 partition? How did you mount the USB drive and the 120GB? Did they just show up automatically (like, when you turned on the computer or plugged in the USB device), or did you do something manually?

---

### Post by ZpiX on 2008-07-14
The 120GB is mounted /media/zpix

and the usb is just connected..

but it works now.. i just deleted all and then i used cmd "sudo nautilus" and change the owner of /media/zpix to my user before i transfered stuff into it..

---

### Post by bobpaul on 2008-07-16
Ok, yeah. That works. I tend to do things manually and I couldn't remember the degree that Ubuntu automated stuff, so I was a little turned about.

Here's a tip: If you make a folder "~/.gnome2/nautilus-scripts/" and put executable scripts in there, they will show up when you right click in nautilus. A good one to start with is "root-nautilus-here", which can be found on the [g-scripts homepage](http://g-scripts.sourceforge.net/cat-executing.php). 

Just save the file "root-nautilus-here" inside that nautilus-scripts folder and make it executable. That way you don't have to 'sudo nautilus' from the command line next time you need to do something like this.

---

