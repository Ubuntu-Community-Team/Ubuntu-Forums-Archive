---
title: "Is there any GUI program that add mp3 files to avi's?"
date: 2008-01-30
forum: Multimedia Production
---

### Post by Dojan5 on 2008-01-30
Okay...
Yesterday i cut together a movie with Avidemux.
When i tried to add an Mp3 file i guess i didn't do it correct, or it wont work.
So now im looking for  another program which adds Mp3 files to a AVI file.
I am going to upload the video to YouTube so the Mp3 file should be there permanently thank you...

Does anyone have a solution to how to add Mp3 files in Avidemux? Or can anyone reccomend a program to do that aside..
Thanks
/
Joel

---

### Post by Creative2 on 2008-01-30
fuoco tools can...

go in eXtra----NEW TRACK FOR MY AVI...

the name of your mp3 file must be the same of your avi file and must be in the same folder of your avi file

---

### Post by Creative2 on 2008-01-30
...i miss link [http://ubuntuforums.org/showthread.php?t=652843](http://ubuntuforums.org/showthread.php?t=652843)

---

### Post by Dojan5 on 2008-01-30
Thanks!
This seem to work...
But i dont understand the command line...
> mencoder INPUT -oac copy -ovc copy -audiofile 'INDIR/BASENAME.mp3'  -o OUTPUT
I think i understans INDIR/BASENAME.mp3 where i guess it should be cl/vid.mp3
but, inpt, should that be the AVI file? like vid.avi?

---

### Post by Dojan5 on 2008-01-30
I ran this in terminal:
> joel@Kissedesigns-2c:~$ mencoder cl/vid -oac copy -ovc copy -audiofile 'cl/vid.mp3'  -o OUTPUT
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Duron(tm)  (Family: 6, Model: 3, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x5fcd1a
AVI file format detected.
[aviheader] Video stream found, -vid 0
VIDEO:  [FLV1]  320x240  24bpp  29.970 fps  255.5 kbps (31.2 kbyte/s)
Audio file file format detected.
[V] filefmt:65536  fourcc:0x31564C46  size:320x240  fps:29.97  ftime:=0.0334
videocodec: framecopy (320x240 24bpp fourcc=31564c46)
audiocodec: framecopy (format=55 chans=2 rate=44100 bits=16 B/s=20000 sample-0)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing index...56f (100%) 1720.26fps Trem:   0min   9mb  A-V:0.033 [255:159]
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  255.469 kbit/s  (31933 B/s)  size: 6133126 bytes  192.059 secs  5756 frames

Audio stream:  160.000 kbit/s  (19999 B/s)  size: 3838955 bytes  191.948 secs
joel@Kissedesigns-2c:~$ 


And something happened...
But, the video didnt get any sound...

---

### Post by Dojan5 on 2008-01-30
Oh!
The missing thing was the output...
Sorry.
And THANKS! This is very useful!!!

---

### Post by Creative2 on 2008-01-30
you can do log with fuoco automatically...any way it's strange...i will see, but mencoder doesn't write errors in that log..so ...it's a bit strange...

---

### Post by Creative2 on 2008-01-30
paste  the output when mplayer plays the result file.

---

### Post by Creative2 on 2008-01-30
...omg maybe you have not understood..that command line was for fuoco tools ...
in a terminal you should do this :

 mencoder INPUT.avi   -oac copy  -ovc copy -audiofile YOURPATHAUDIOFILE.mp3  -o OUTPUT.avi

---

