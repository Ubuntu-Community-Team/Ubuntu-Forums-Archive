---
title: "VOB file merger for Linux?"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by spazsui on 2008-01-30
Hi, I've been looking thru the forums and googling too but can't seem to find a definiive answer to this issue.  Maybe I glazed on over it.  Is there an application in Linux that can take vob files and merge them into one single vob file?  I know the Windows world has a couple of programs that do just that.  And I don't mean a program that extracts the files and then merges them like Ammon's  DVD2HDD.  I mean a program that takes vob files that are already on your harddrive and just combines them into one file.  Something like the windows program VOBMerge.  Just looking for a linux equivalent.   Any and all help is greatly appreciated!   :)

---

### Post by philc on 2008-01-30
For a command line tool, FFmpeg will do this in combination with the "cat" command. There may be some limitations on the file types that this will work for, but I think VOB files might be OK.

Here's a link:

[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004611.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004611.html)

Otherwise for GUI options, look into Avidemux which should do this. 

Or for a more traditional video editor approach, [Open Movie Editor]("http://openmovieeditor.sourceforge.net/HomePage"). It's very easy to add multiple clips to the timeline, then render (transcode) a new file to your desired format.

I think there's probably lots more options too.

---

### Post by spazsui on 2008-01-30
Thanks!  I will look into those suggestions and see if they work for me.  Great help!

---

### Post by michaelzap on 2008-01-30
AviDemux will merge them into an mpg or other file format, so depending upon what you want to do with the merged file that might be the easiest way to do it.

---

### Post by disturbedite on 2008-01-30
yeah, avidemux can do this.  you set the container to MPEG Program Stream (PS) and then just rename the extension to VOB if you want.

---

### Post by disturbed1 on 2008-01-30
cat file01.vob file02.vob >newfile.vob

mpgjoin file01.vob file02.vob -o newilfe.vob

mpgcat file01.vob file02.vob -o newilfe.vob

mpgtx -j file01.vob file02.vob -o newfile.vob

You can also look into GOPChop and/or DVBCut, 

vobcopy -i /path/to/ripped/dvd/files/VIDEO_TS -n1 -l -o /path/to/put/files/file.vob

^^ -i = input path. The complete path
-n = title number, if your not sure, use lsdvd or vobcopy -i /path/VIDEO_TS -I
-l enables large file support.
-o is the path to output the files.
You can also use vobcopy to rip from the DVD driver.

---

### Post by Maxei on 2008-03-18
Hi, there seems to be a simple solution, which I was looking for a while before. Just to mention that I usually rip my DVDs with dvdbackup into my hard-disk. Then I use DVDShrink with wine to, well, make 4.7 GB pieces of the DVD. You see, I don't like to compress the movie because of loss of quality. What I do is to backup in 4.7 GB discs, as many as it can take, usually 2, and rarely 3 discs when it is a big, big movie that was made in two original DVDs. In this latter case, I use also DVDShrink to add more VOB files to the preceeding ones, using the re-author function, so I can browse to get the next VOBs in the hard disk. So to make the first disk backup is no problem. It is in the second disc when I have to join vobs from two original DVDs. Hope this helps.
Maxei

---

### Post by spazsui on 2008-04-21
These are all great options folks!  I definitely appreciate all the answers!

---

### Post by bluepowder7 on 2008-06-11
recent thread, so hopefully i can add a question since mine is very much related.  will those cat / mpgjoin / mpgcat commands work to join VOBs into one larger VOB which i can then run through an H264 encoder?  is there some header / end-of-file stuff i need to worry about?

---

