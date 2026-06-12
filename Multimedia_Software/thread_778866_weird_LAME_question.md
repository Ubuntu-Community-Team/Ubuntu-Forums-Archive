---
title: "weird LAME question"
date: 2008-05-02
forum: Multimedia Software
---

### Post by andrewc2005 on 2008-05-02
Ok, this is kind of a weird issue, but I wasn't paying too much attention to the command line options I set for LAME in grip, and ended up ripping and encoding a significant number of CDs with a variable bit rate (at V0) AND a minimum bitrate of 320k.  Kind of pointless.  

I then tried ripping two files with CBR and a minimum bitrate of 320k just to see the difference, and the file it created was exactly the same size as the VBRed one.  So then I use the cmp command to see what the difference was and I got:
[the first two files] differ: byte 2080, line 2
[the second two files] differ:  byte 2289, line 2

I know very little about the actual mp3 format; does this byte designate whether it's CBR or VBR?  

I know it seems strange to obsess over a single byte, but I wanted archive quality for these songs, so I was hoping for perfect encoding, and like I said I know very little about the mp3 format so I'm not sure if there will be any difference in how mp3 players handle the files.  I tried playing both in VLC and the VBRed one seems to use slightly more processor time, but top is sufficiently imprecise that I couldn't be sure.

---

### Post by disturbedite on 2008-05-02
if you want to use a lossy format, i'd recommend ogg, since its FOSS.  but its better in more than a few ways.
i personally use flac.  use it if you want true cd quality.
but if i have to use mp3, i use certain settings.  (it drives me nutty that people use those stupid presets).
i use 320 CBR Stereo (NOT joint stereo, which was a stupid implementation) if i do have to use mp3 for some unusual reason.

---

