---
title: "Amarok skipping first few seconds of song"
date: 2008-05-20
forum: Multimedia Software
---

### Post by laszlo462 on 2008-05-20
As the title says, Amarok seems to be skipping over the first few seconds of the next song in the playlist before it begins playing it.  Crossfading is off, and there is no gap set between songs.  I also turned off OSD to see if that had something to do with it, but still no difference.  Has anyone else noticed this?  When OSD is on, it shows the next song title a few seconds before the current song is done, so it's like Amarok has begun playing it without outputting the sound.  Could this just be an issue with the wma or mp3 codecs?

Thanks,
Steve

---

### Post by laszlo462 on 2008-05-22
Nevermind.  The problem lies in the fact that the music files are on an NTFS partition.  Copying over a few albums to the local ext3 partition plays through just fine.

---

### Post by perrti-y02 on 2009-05-10
I would like to restart this thread because I have the same problem but with songs on an Ext4 partition. It only skips the start of some songs, but I cannot see a pattern. All my library is in flac and I am using Amarok 1.4.10 on Ubuntu 9.04.

---

### Post by JK3mp on 2009-05-10
Why not just put them all on the local partition????

---

### Post by perrti-y02 on 2009-05-10
What do you mean the local partition? The same one as /? I keep all my music and video on a separate partition (but the same hard drive) because when I need to reinstall my system (which happens about every 3 months) I can format / and keep /home and /data (2 separate partitions).
Basically it makes reinstalling easier.

---

### Post by laszlo462 on 2009-05-10
Do you have an ext3 partition at all?  I'd say try playing a few songs off of an ext3 partition, maybe there's something with the ext4 filesystem causing that.

---

### Post by perrti-y02 on 2009-05-11
Ext4 did work for me until I needed to do a reinstall. It is also very intermittent in that it isn't doing it now and only ever does it once in a blue moon.

---

### Post by perrti-y02 on 2009-05-11
It still skips on an ext3 partition. I also appear to be unable to fast forward or rewind. I think this might be related but that is based on nothing solid.

---

### Post by sena-sena on 2009-06-03
I had this problem as well, but it seems to have gone now.
A friend suggested that I speed up amarok by following [this tutorial]("http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html"), and this seems to have also fixed the problem of amarok skipping the start (and end) of songs.
Hope this helps :)

(btw, running amarok 1.4.10, ubuntu intrepid and my music is on a seperate partition)

---

