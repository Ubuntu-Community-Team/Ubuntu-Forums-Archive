---
title: "Rhythmbox can't access files on NFS mount"
date: 2008-02-04
forum: Multimedia &amp; Video
---

### Post by jazzgossen on 2008-02-04
I have an NFS share with a bunch of media files. I can see and play the files with Totem and Audacious, but when I point my Rhythmbox library to that directory, I only get errors under the "Import errors" tab:
Can't access file:///home/martin/Music/music%20on%20undertow/Mr%20Bungle/Backstrokin.mp3 
... etc.

Does rhythmbox need write permissions? Or can't it handle links or spaces in file names? Or something else?

---

### Post by jonholio on 2008-04-25
Hi there,

I have just updated to Ubuntu 8.04 with Rhythmbox 0.11.5 and have the same problem as you had. I renamed one of the files to have no whitespace and it imports fine. Did you find a solution?

---

### Post by BjBlaster on 2008-05-29
I had troubles with it too, it would play one song via nfs, then lock up my soundcard and the app. It's ok via locally stored songs, just terrible on nfs. I use Audaicous now. It's not as nice to use (a bit like old winamp), but it works fine with nfs.

---

### Post by jazzgossen on 2008-07-06
I still have the same problem on Ubuntu 8.04. And it's just not Rhythmbox. 

I have an NFS share (on a FAT32 partition) that I can access, and all files have rwxrwxrwx access and are owned by root. I can read and write files, but whenever I try to play a movie, I get a "Stream contains no data" error message. If I copy the file to a local drive, I can play it without problems. It's the same even if the path to the file and the file itself contain no spaces.

Below is an example output:

$ totem movie.avi
** (totem:10354): DEBUG: Init of Python module
** (totem:10354): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:10354): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:10354): DEBUG: Creating Python plugin instance
** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

---

