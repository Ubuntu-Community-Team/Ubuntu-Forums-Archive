---
title: "iPod Classic will not sync with Banshee"
date: 2009-12-02
forum: Multimedia Software
---

### Post by cj.surrusco on 2009-12-02
I was able to get banshee to recognise my 120gb ipod today by using "killall -9 nautilus", then plugging the ipod in and running nautilus again. I rebuilt the database as it suggested and it was able to see all of the songs that I had on it. I removed all of them so that I could sync it with my new library in Banshee.

 When I chose to sync my music, it appears as if they are transferring. There is a box in the bottom left corner that says "syncing CJ's iPod" or something similar. The songs scroll by as they are "transferred". Once it is done, Banshee shows all of the songs that are on the ipod and that 13 gb are taken up by music.

I unplug my iPod, and there is absolutely nothing on it. In the about section, it shows that there is only about 114mb used for "other". When i plug it back into Banshee, it shows as an empty ipod, and starts "syncing" again.
 
Does anybody know what could be causing this problem?
Thanks,
CJ

---

### Post by sabauma on 2009-12-04
I seem to have a similar problem. _Most_ of my music will sync with my iPod just fine, except for the music that it transcodes (mostly from FLAC). It still claims to transcode the music and takes a while doing it. The transcoded music even shows up through Banshee right after the syncing. When I eject and look on the iPod though, the music is missing and won't show up in Banshee again after it is plugged back in. 

This seems to be a recent development as it did not happen before I upgraded to Karmic. I believe I was using the same version in Jaunty. 

Also, it will add the tracks if I manually add them one at a time.

---

### Post by cj.surrusco on 2009-12-04
I don't think one at a time will work for me... I have over 2,000 songs. Is there any other way to fix this? Or should I downgrade back to Jaunty?

---

### Post by sabauma on 2009-12-05
Personally, downgrading would be my last resort. I would recommend trying Amarok and see if that works. Amarok 2.0 has iPod support, as long as you don't need to transcode anything. If that doesn't work or you need transcoding, Amarok 1.4 works and has scripts for transcoding files during transfer, but it is not in the normal repos.

---

### Post by unteer on 2010-01-24
Check to make sure that your iPod is mounted with correct owner (your user) and permissions (rwx for user).  I am experiencing the same problem.  I think the problem is that Banshee is not, "failing gracefully," and even though it thinks it is syncing, because it does not have write permissions to the iPod disk, it cannot actually committ any changes, and thus nothing syncs.  Just a thought, give it a look.

---

### Post by rol7805 on 2010-01-31
I'm having the same problem. I'm on karmic with the latest build of Banshee (1.5.3) and a 120 GB iPod classic. I had to do the same killall -9 nautilus trick until the new build of Banshee. Previously the sync would just hang but the new Banshee build told me which songs had errors (one had a zero length playtime for some reason and the other had a bad cover art image). Once I removed those from Banshee, the sync "finished". I can even play a song from the iPod. The disconnect in Banshee still doesn't work with an iPod, so I ejected at the Gnome level. I'll check permissions on the mount and see if that's the problem.

---

### Post by unteer on 2010-02-01
Ok, so here are some other tidbits I have uncovered when trying to get this problem set up.

1) If you iPod is formatted, "For Mac," meaning using either HFS or the HFSplus filesystem, then sometimes when you unmount it incorrectly it will damage the filesystem and it needs to be cleaned using fsck.hfs or fsck.hfspus depending on which filesystem your iPod is.  You can see if there are errors mounting the iPod if you run the dmesg command and check for the section where it attempts to mount the disk.  If you have just plugged the device in and your computer had already been booted, simply run dmesg | tail -20 to get the proper information.

2) If you are like me, then maybe in all of your futzing around with the iPod you have somehow, miraculously deleted the iPods UUID (unique universal identifier).  This is a number that the computer can use to manage your iPod individually, and many applications and OS use them for things such as automounting a device to the same directory every time.  This allows you to write specific FSTAB entries for mounting, without needing to specifier a device node (ie /dev/*).  This might allow you to force mount in RW despite damanged FS (see first point), but without the UUID it becomes more a nuisance than a solution.

So what did I end up doing?  The crappy solution.  I brought my iPod to a friends house who has windows and formatted it using the official iTunes software.  This rebuilt the filesystem in VFAT (which is arguably a less ideal Filesystem for mass media devices than HFS), and even downloaded the latest firmware patch.  Upon bringing it back to my ubuntu install, it was automatically detected, banshee synced, and I no longer need to worry about corrupting the HFS system so easily (though it's just as easy to accidentally corrupt a VFAT methinks).  

At least its all working now, and banshee can sync again.

Hope this helps anyone who stumbles on the thread, as I have been working at this for years without anyone ever answering the questions with their solutions.

---

### Post by cj.surrusco on 2010-02-21
I've resorted to syncing the ipod through rhythmbox. I am very happy with this alternative except for the fact that album artwork does not work correctly. But, the songs transfer over quickly without any bugs like banshee. The cover art is only showing for the songs with the image embedded in the mp3's. Even though the plugin for cover art is checked, the covers are not being downloaded from the internet.

---

### Post by uclicktu on 2010-12-18
So here is the deal: 
I have a 4th generation ipod and had it connected up to OSX initially before finally moving everything to linux (the almighty BUNTU). Anyway, the issue seems to revolve around the way OSX sets up there file system. Apparently they use journaling which is a feature that helps protect the files system against power outages or hardware component failures, reducing the need for repairs.... WHATEVER... anyway HERE IS WHAT WORKS::

[LIST=1]
[*]Connect the iPod to a Mac (feel free to quit iTunes)
[*]Start up "Disk Utility"
[*]Select the iPod (the volume, not the disk - the one that has the same name as your iPod)
[*]Turn off Journaling under the File menu. On post 10.4 Macs you need to hold down the option key when selecting the file menu in order to see this option.
[*]Eject.
[/LIST]
**<blink>SHOOT old osx/apple propitiatory crap in hard drive</blink>**!

---

