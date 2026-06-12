---
title: "Mounting hardrives"
date: 2009-04-13
forum: Mythbuntu
---

### Post by timswait on 2009-04-13
I've just installed Mythbuntu on a system which I also have XP on. If I get to like Mythbuntu I might get rid of windows, but for the moment I'd like to keep it. I have my hardrive with a Windows partition, a Mythbuntu partition and a documents partition on which I have home movies. How do I add the home movies directories to Mythbuntu? At the moment I can't even mount either the windows partition or the documents partition (they're both formatted as NTFS) I get the following error:

"Unable to mount Documents
Failed to execute child process "gnome-mount" (No such file or directory)"
What does this mean?

---

### Post by MonsterMaxx on 2009-04-13
the first thing you'll do is find out how to address the partition.

sudo fdisk -l

This will give you a list of 'devices'. You'll have to figure out which is which, sometimes just by mounting it and looking inside.

Let's say you will guess it as /dev/sba2

To mount a drive you must have a place to mount it and then the command to mount it

so first

sudo mkdir /mnt/newdrive 

then you mount the drive

sudo mount -t cifs /dev/sba2 /mnt/newdrive

That should mount it so that when you change into the /mnt/device directory you are looking at the windows drive.


fyi 
sudo umount /dev/newdrive
will unmount the drive. In case you guessed wrong when you were figuring out which was which - you need to unmount it before you can try another.

hope that helps

---

### Post by AboveTheLogic on 2009-04-15
I'm partial to mountmanager:

sudo apt-get install mountmanager

makes it much easier, and it will mount by HDD serial instead of /dev path (I found this to be more reliable)

---

### Post by timswait on 2009-05-25
I can't get mount manager to work. I've installed it and it appears on my menu, but when I click it all that happens is a box comes up that I enter my password into, but nothing else.
I've tried mounting the recordings folder at boot using fstab. I've added the following line:
```

/dev/hda1   /mnt/rec  ntfs-3g  ro,auto,user,fmask=0111,dmask=0000   0    0
```
It does now mount the disk to the /mnt/rec directory and I can see my recordings when I browse to it with nautilus. However when I add it in Myth as a storage directory it says "/mnt/rec/MyVideos is not writable" and none of the recordings in that folder are visible in MythTV. What have I done wrong?

---

### Post by Chris Musampa on 2009-05-25
> **timswait said:**
> I can't get mount manager to work. I've installed it and it appears on my menu, but when I click it all that happens is a box comes up that I enter my password into, but nothing else.
I've tried mounting the recordings folder at boot using fstab. I've added the following line:
```

/dev/hda1   /mnt/rec  ntfs-3g  ro,auto,user,fmask=0111,dmask=0000   0    0
```
It does now mount the disk to the /mnt/rec directory and I can see my recordings when I browse to it with nautilus. However when I add it in Myth as a storage directory it says "/mnt/rec/MyVideos is not writable" and none of the recordings in that folder are visible in MythTV. What have I done wrong?
ro = read only

---

### Post by timswait on 2009-05-25
Aha, thanks. Have now changed it to rw. There's now no error message when I assign these as Storage Directories in the Backend setup, however the files which are contained within them still do not appear in the Media Library in the Frontend. When I go to Watch Videos or Image Gallery (there's avi's, mpegs and jpegs in those folders, and I can open them with nautilus) it just comes up with no files found. What's up with it now?

---

### Post by timswait on 2009-05-25
Is there some command needed to make it index the contents of the storage directories?

---

### Post by AboveTheLogic on 2009-05-25
you gotta set the directory, then go into video manager so it searches the directory you set and populates the database with the files that "watch videos" will play

Also, I probably would have done this:
```
/dev/hda1   /mnt/rec  ntfs-3g  defaults   0    0
```

---

### Post by timswait on 2009-12-28
i've come back to this after a while, but I still can't get the videos to appear in Myth. I have modified fstab to mount the second hardrive at /mnt/docs. On this drive there is a folder called oldrecordings, and one called homevideos. If I open a browser window I can browse to /mnt/docs/oldrecordings, double click a file and it plays in VLC just fine, likewise with homevideos. I have set a storage group under videos in the Backend to include /mnt/docs/oldrecordings and another one for /mnt/docs/homevideos. I get no error messages when I leave Backend setup. I have gone in frontend utilties and setup>setup>Media Settings>Videos Settings>General settings. I have added /mnt/docs/oldrecordings:/mnt/docs/homevideos (tried with and without a space after the colon), but still when I go to Video Manager or Watch videos, it says No files found. What am I missing?

---

### Post by neanderthalman on 2009-12-28
I was tearing my hair out over the same thing.  Had the drive mounted, I could play in VLC, but the video manager and watch videos showed me nothing.  While hunting down an unrelated problem, I stumbled on a post that fixed it.

This was the solution:  Go to the video manager and press "M" to open the menu.  In that menu, there's an option to scan for video files.  

I seem to recall this being automatic with 8.10, but with 9.10 it's not.  I don't know about 9.04, but it's so simple that it's worth a try.

---

### Post by timswait on 2009-12-28
OK thanks, that's got it

---

### Post by timswait on 2009-12-28
Oh dear, now I've just fiddled with it and messed it up even more! I've ended up mounting the second harddrive at /var/lib/mythtv, and putting all the relevant folders in it. I think I've set all the ownerships correctly (although how do I check it?). The problem is that in all the copying folders across I deleted some recordings in the process, but now Myth still lists them in the recordings list and refuses to delete them form the list, even though they're not in the folder anymore. And now a more serious problem is that no new recordings appear in the recordings list. The recordings are made, they are in the correct folder and they play with VLC, but they don't appear in the list. Is there someway to force the list to update to not include the deleted files and include the new recordings? I've run he backend and let it fill the database and I've clicked the "Optimise Tables" button in MCC but it makes no difference.

---

