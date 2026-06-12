---
title: "Banshee refuses playback after reboot"
date: 2010-11-22
forum: Multimedia Software
---

### Post by The Wish Within on 2010-11-22
Hi.

I've downloaded Banshee to listen to my music.
At the beginning I had problems with playing MP3 files.
I've downloaded the gstreamer fluendo mp3 plugin. 
After that, everything was fine.
Then after I have rebooted my notebook, Banshee suddenly refused the playback of any song! Then I deleted all songs from the playlist and reloaded all songs.
And suddenly I could play all songs again after readding them to my playlist...
I rebooted again and Banshee refused it again!
(Instead of playing the song, just the X appears.)

I don't want to reload my songs everytime I want to use banshee.

What's the problem?

(All songs are on another HDD and I have Ubuntu 10.04)

I hope someone can help me.

~The Wish Within

---

### Post by The Wish Within on 2010-11-26
Sorry for pushing but I really need help...

---

### Post by londonkeith on 2010-11-26
You need to mount the second HDD music file so Banshee sees it as a local file. Firstly make a mount point in a terminal e.g. 

sudo mkdir /media/musicfile        (any unique name will do)

Then add a line to fstab. It will be something like this

sudo gedit /etc/fstab

add

/dev/sdb1  /media/musicfile  ntfs-3g  defaults  0  0

The first bit is the second HDD music file location, followed by your defined mount point, followed by the directory format (could be ext4 etc). 

Now when you boot the music should be seen automatically. Worked for me. Make sure that there is no space at the end of the line and if you're using a gui text editor a empty line at the end.

---

### Post by The Wish Within on 2010-11-27
Do I have to replace /dev/sdb1 with /media/DATA/iMusic if my music is in /media/DATA/iMusic?

//Edit: Everything OK. Seems to work. Thanks. (Didn't replace anything)

---

