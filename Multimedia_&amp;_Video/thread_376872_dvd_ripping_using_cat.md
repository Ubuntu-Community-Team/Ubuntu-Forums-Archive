---
title: "dvd ripping using cat"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by Vincent_Lin on 2007-03-05
Dear all,

I have tried a number of software to rip dvd conntents onto harddisk - dvdrip, VIVE, vobcopy, etc..  Each of these applications holds some advantages and some issues.  For example, vobcopy is the easiest one to get the "longest" title from the DVD disk to harddisk.  However, I can't figure out how to set the language options.  Sometimes, the ripped vob files has Spanish track, instead of English track that I want.  Sometimes, the logest (most chapters count) might not be the actual "moive" track that I want.  So, sometimes I run dvdrip first to figure out the numbers of titles I want to rip, and check the audio language as well, before I vobcopy out the title that I want.

Recently I tried an even "basic" method - cat.  I can run the following command, assuming /dev/hdc is my DVD drive - $cat /dev/hdc > movie.iso" to get all the contents out of a DVD.  I have successfully ripped 4 or 5 DVD disks using this method.

I had learned that vlc player can actually play an iso file, provided that this iso file is an exact copy of the disk.  

It is also very eacy to configure mythtv to use vlc to play these iso's, with vlc commandline options including setting up keys to perform "Exit", "Fast Forward", etc, eto match mythtv key sequences.  I have not explored the whole possibilities of all the key definitions as of yet, such as "Rootmenu", etc...

My problem is: some of the disks could not allow me to $cat /dev/hdc > something.iso, and the terminal gives me IO error for cat command.  Subsequently, gxine and mplayer can still play these disks without issues though.

And my question is, naturally - what is the cause of such IO error, and is there any options for cat command to force the reading from DVD disk, without causing such IO error?

Or, is there a commandline option for vobcopy to specify language track selection?

Thanks.

Vincent

---

### Post by markitect on 2007-03-05
Id suggest using dd, its main use is images, although I've never used it to copy a DVD something like
```

dd if=/dev/hdc of=image.iso

```
theres also options for specifying block size and things like that, but they usually aren't that helpful

---

### Post by Vincent_Lin on 2007-03-05
Thanks.

I forgot this command.

I will try it out with the trouble-d DVD to see how it works.

Vincent

---

### Post by Vincent_Lin on 2007-03-06
Sorry that dd also faild, same message.

So I tried vobcopy -m, to mirror DVD disk onto harddrive.  

The process stopped/halted at a tiny file, then vobcopy decided to ignore it and moved on to finished the mirroring.

I did not investigate further, maybe I should have - using dd to create an iso,  and play the iso to see how it works.

So I think the problem is due to the disk itself.  Could it be designed as some sort of copy-protection scheme?  Just wondering.

Thanks. 

Does anyone know how to select language track with vobcopy commandline options?

Vincent

---

### Post by markitect on 2007-03-06
You might want to check out fixvts  they claim it works under wine, although i haven't tried it myself.  The latest trend it to put crc errors onto the disc in areas that dont get played by the player, so its only a problem with you try copying all the files instead of just the content, and this program gets the content rather then the entire file.

---

### Post by Vincent_Lin on 2007-03-06
So I suspected.  Thanks.

Vincent

---

### Post by Vincent_Lin on 2007-03-07
After another search in ubuntuforums, I found that this issue is well known - as real copy-protection "features" that Sony and Disney, and others, use on their rather new DVD disks.  And the solution is out there too - a pointer to ripit4me.org shows all the issues and solutions.  

Unfortunately, the solution is based on Windows and wine is needed to make it work.  Fortunately, it is composed of all free software.  It is inteesting that this website also mentioned how it works under wine.  And a direct Howto for Edgy users is presented as well.

I will try it and report back soon.


Vincent

---

