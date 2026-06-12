---
title: "Reinstalling Mythtv from scratch, how to save recordings?"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-03-09
Well after a week of reading, posting, and getting somewhere (but not restoring function to my myth box) I have come to the conclusion that I need to wipe the slate and redo the whole thing.

The last straw was when I did a test recording from each card the recording wouldn't open using mplayer.

mysql data seems to be lost, i have 219.4 gig of recordings that do not appear within mythtv, but are visible in the file system.

I can copy the recordings to a usb drive, but how do I reload them into mysql when i complete reinstalling mythtv?

Is there a player to view the recordings outside of mythtv?  If I can view the recordings, I can delete many of them and not have as much to save and reload.

Thanks in advance.

---

### Post by superm1 on 2007-03-09
Sorry to hear about the troubles with your database corruption.  
The recordings are directly viewable outside of mythtv with any player.  Typically they are mpeg2 files or RTJPEG.  Trying any of mplayer, VLC, or xine should work.

Before jumping to the conclusion that they are still there (if you've tried to play them outside of mythtv), have you rebooted the system lately?  This would be a sure way to verify that any programs that have a lock on the files release it.  If they still dont work, then boot up a live disk and run a fsck on the filesystem.  You might have corruption worse then expected.

As for getting them back into the database, I know there is a contrib script out there that will import the recordings back into the database, but you will be missing out on all of your metadata from before.  Its a pain in the *** to refill out information for all these shows that you won't know much about.

---

### Post by wjston on 2007-03-09
> **Panhead Bill said:**
> 

Is there a player to view the recordings outside of mythtv?  If I can view the recordings, I can delete many of them and not have as much to save and reload.

Thanks in advance.

Why don't you burn them to dvd? I use ProjectX for editing out commercials and then Qdvdauthor for creating a simple menu and burning to dvd. 

It took me a bit of time to figure out how to use ProjectX, but now I can transfer 2 one hour episodes, including editing out commercials, creating a simple menu and burning to dvd in under 1 hour. My system is only running on a 3.06 Celeron, so I'm sure you could probably transfer your recordings in a reasonable amount of time before you rebuild your Myth Box. Also, I do all my conversion in Ubuntu, not MythTV. I tried using Mytharchive but all my recordings were out of sync, so I tried several forum suggestions to remedy this but none worked. 

Once you rebuild your system and have it functioning the way you want. use Synaptic Package Manager and install Mondorescue to create a set of backup dvds to reinstall your system in the event of a corruption.

I am going away for a few days but will be monitoing this forum if you decide to create dvds of your recordings.

Best of luck to you.

---

### Post by Panhead Bill on 2007-03-09
SuperM1:

The files should be in mpeg2 comming from the Hauppague 150 and 350 cards.  I tried to view them using mplayer but no go.  I'll try a few files instead of one, and whatever players I can fire up.  

Are the mpeg2 files viewable on a Windoze machine?

In my search to fix the things borked by the updates, I had the dreaded database error, lirc error, socket error, blank database, my port was changed to 3303, and my mouse now requires several clicks or a 2-3 second hold on left click for some things to activate.  I have restarted the box and shut the box down several times in trying the fixes I found in this forum.


wjston:

As for burning to disk, I had not reached that point on my box.  It scheduled, recorded, played back and I had the remote working (I needed to program a couple of additional keys though). 

I have a couple of hard drives 100 and 120 gig that I can put into an external usb box to copy the files, and the cost of the dvd's for what will be one time viewing would be a waste of my meager funds.  So If I can view the recordings on Windoze XP or even a spare machine with Ubhuntu on it, I can then erase almost all of them.

P.S.  An attempt to read the recordings from Ubuntu desktop (Gnome).

Gxine playes the recordings, grainy and without sound. 
Totem movie player error: "You do not have a decoder installed to handle this file.  You might need to install the nessisary plugins ."
Mplayer error:"error opening/initializing the selected video_out (VO) device.

---

### Post by superm1 on 2007-03-10
> **Panhead Bill said:**
> SuperM1:

The files should be in mpeg2 comming from the Hauppague 150 and 350 cards.  I tried to view them using mplayer but no go.  I'll try a few files instead of one, and whatever players I can fire up.  

Are the mpeg2 files viewable on a Windoze machine?

In my search to fix the things borked by the updates, I had the dreaded database error, lirc error, socket error, blank database, my port was changed to 3303, and my mouse now requires several clicks or a 2-3 second hold on left click for some things to activate.  I have restarted the box and shut the box down several times in trying the fixes I found in this forum.


wjston:

As for burning to disk, I had not reached that point on my box.  It scheduled, recorded, played back and I had the remote working (I needed to program a couple of additional keys though). 

I have a couple of hard drives 100 and 120 gig that I can put into an external usb box to copy the files, and the cost of the dvd's for what will be one time viewing would be a waste of my meager funds.  So If I can view the recordings on Windoze XP or even a spare machine with Ubhuntu on it, I can then erase almost all of them.

P.S.  An attempt to read the recordings from Ubuntu desktop (Gnome).

Gxine playes the recordings, grainy and without sound. 
Totem movie player error: "You do not have a decoder installed to handle this file.  You might need to install the nessisary plugins ."
Mplayer error:"error opening/initializing the selected video_out (VO) device.
I know for sure that mplayer can play these recordings.  It sounds like you had another video player active (or crashed) when you tried to use mplayer.

They are viewable on a windows machine, but I would recommend using a video player that handles the aspect ratio correctly such as VLC or media player classic.

it really sounds like this machine took a beating if this many things got messed up.  I would really doubt that an update would change so much.  I'm leaning much more towards some sort of corruption or hardware troubles.

---

### Post by Panhead Bill on 2007-03-10
Well the other day I quit out of Myth in order to fire up firefox.  I do that often so I can check the forums for answers to specific problems I'm working on.  

There were updates available, so foolishly I updated and restarted.  at that point my woes began.  I had the database error, lirc, and who knows what else.  I tried the fixes for the database, but i seemed to be chasing my tail; mysql did not appear to be running, but the start command was rejected as the database WAS running, sort of.  I ran the updates for IVTV and LIRC, but nogo.  I find it somewhat unlikely that both cards would fail, or the LVM drives would get corrupted, while doing updates through the update manager.  I could be wrong, though.  

To find out I have to do a fresh install of Edgy, and build Myth from scratch.  I will test all along the way and most likely will regain control of the box.

To do things smarter this time, I am thinking about some form of dual boot,  partitioning, and backup that will allow me to have two installs of myth; one as the running version, and the other as the "new" tweaked version.  Ultimately the new version would be copied to the running version partition and the process would repeat.

Since I am running a 4 drive LVM for video storage separate from the system drive, I am trying to learn enough to determine what partitioning scheme would work on the system drive.  I installed the default partitioning scheme from the live disk.

My "system" drive is 80 gigs and currently about 8.3 gigs is used.  I believe that the swap partition can be shared.  Should I partition the rest iof the drive into two (Running and Tweeked) or can any parts of of the ubuntu desktop and myth installs be common to the "tweeked and running" partitions?   I'm asking that question after reading of a partition scheme with separate  /ubuntu  and /user partitions to allow for kernal updates.
(Yes, I'm in way over my head at this point)

After finding a suitable dual boot partitioning scheme, (Ubuntu desktop/Mythtv -  Ubuntu desktop/Mythtv), what method would allow me to copy the "tweaked" partition over to the "running" partition after changes heve been successfully made and tested?

---

### Post by superm1 on 2007-03-10
> **Panhead Bill said:**
> Well the other day I quit out of Myth in order to fire up firefox.  I do that often so I can check the forums for answers to specific problems I'm working on.  

There were updates available, so foolishly I updated and restarted.  at that point my woes began.  I had the database error, lirc, and who knows what else.  I tried the fixes for the database, but i seemed to be chasing my tail; mysql did not appear to be running, but the start command was rejected as the database WAS running, sort of.  I ran the updates for IVTV and LIRC, but nogo.  I find it somewhat unlikely that both cards would fail, or the LVM drives would get corrupted, while doing updates through the update manager.  I could be wrong, though.  

To find out I have to do a fresh install of Edgy, and build Myth from scratch.  I will test all along the way and most likely will regain control of the box.

To do things smarter this time, I am thinking about some form of dual boot,  partitioning, and backup that will allow me to have two installs of myth; one as the running version, and the other as the "new" tweaked version.  Ultimately the new version would be copied to the running version partition and the process would repeat.

Since I am running a 4 drive LVM for video storage separate from the system drive, I am trying to learn enough to determine what partitioning scheme would work on the system drive.  I installed the default partitioning scheme from the live disk.

My "system" drive is 80 gigs and currently about 8.3 gigs is used.  I believe that the swap partition can be shared.  Should I partition the rest iof the drive into two (Running and Tweeked) or can any parts of of the ubuntu desktop and myth installs be common to the "tweeked and running" partitions?   I'm asking that question after reading of a partition scheme with separate  /ubuntu  and /user partitions to allow for kernal updates.
(Yes, I'm in way over my head at this point)

After finding a suitable dual boot partitioning scheme, (Ubuntu desktop/Mythtv -  Ubuntu desktop/Mythtv), what method would allow me to copy the "tweaked" partition over to the "running" partition after changes heve been successfully made and tested?
Thats quite a bit of work to have two installs going in parallel.  I have a feeling this is more than you will want to go through. 

The better idea here, is to get a good setup going, and back it up daily.  Set up something that rotates the backups weekly.  So if you change one thing or update one thing, you can always revert back to another backup.

---

### Post by Panhead Bill on 2007-03-10
What backup programs would you suggest?

Would the backup scheme have save me from the 47 updates from the update manager that (i believe) started my problems?  In other words would it be able to restore the state  of the system to what it was just before the multiple updates?

---

### Post by superm1 on 2007-03-10
> **Panhead Bill said:**
> What backup programs would you suggest?

Would the backup scheme have save me from the 47 updates from the update manager that (i believe) started my problems?  In other words would it be able to restore the state  of the system to what it was just before the multiple updates?
Well there are two things i'd recommend you look into: sbackup and partimage.  Partimage lets you make an image of the whole partition, sbackup will backup all settings, installed packages and files that you want.

Personally, I use sbackup, but i've gotten really lazy lately.  My network has been reorganized, and i havent backed up in a month (knock on wood :))  Partimage probably works better for what you would want (everything in the state it was at the last backup), but makes very large backup images.

---

### Post by Panhead Bill on 2007-03-10
Thanks for the info. 

 Now to copy the recordings and start over on the box.  Oh well I have a new video card, sound card, and more memory to install, and I want to lap the processor heat sink while the case is open.

---

### Post by majoridiot on 2007-03-14
once you get your recordings backed up and restored to where you want them, install mythvideo:

```
# sudo apt-get install mythvideo
```

and when you set it up (it adds frontend menus), point it at the director(ies) that have your shows.  if 
they are all shows recorded by mythtv, it will use its internal player, so no external player is needed. 

that will give you a good interface for watching/managing the ones that the DB dropped.

---

