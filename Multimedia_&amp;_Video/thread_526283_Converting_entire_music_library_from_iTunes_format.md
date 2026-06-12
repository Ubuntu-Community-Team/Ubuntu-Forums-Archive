---
title: "Converting entire music library from iTunes format"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by bbqsauced on 2007-08-15
I've ordered the parts to assemble my new computer, and I plan on using an old 80g hard drive as a storage drive.  Since I want to dual boot both windows and Ubuntu, I wanted to be able to access my music on both OS's without having two copies of my entire library, since it is quite large. (>10gb)

My friend told me to just format the 80gb drive as FAT32, and both OS's would recognize it.  The problem is, most of my music is in iTunes, and I'm not sure what is available to play or convert these files.

If possible, I'd like to convert them all from the iTunes format so I can use a different media player in Windows as well.

Anyone have some insight on this?

---

### Post by duffrecords on 2007-08-15
The word on the street is that there is a version of Winamp available for Linux now.  Winamp can play the AAC format used by iTunes, so you shouldn't have to convert your library.  On a side note, since AAC uses lossy compression, converting your files to another format would further compress (and degrade) the audio.  Try to avoid that option if you can.

You may still run into problems with DRM-encoded files, however.  There are software packages available to remove such restrictions.  Try a Google search for "remove DRM."

---

### Post by benerivo on 2007-08-15
You will lose some audio quality by transcoding from aac to mp3. To transcode, you can use a few packages available in the repositories such as 'soundconverter' or 'nautilus-script-audio-convert'.

If you have the original CD's I would strongly recommend ripping them again in to either mp3 or ogg. With mp3 you are guaranteed to have them play anywhere (ie the cd player in your next/first car), which is a big advantage.

Having said that, most windows and linux music libraries/players will play aac files, so you can just keep them in that format if they were not from CD. I've got no idea about DRM and what effect that might have on your ability to play them back or even transcode them.

Also I would have the drive formatted as ntfs as linux can read/write to that filesystem using the popular ntfs-3g package.

---

