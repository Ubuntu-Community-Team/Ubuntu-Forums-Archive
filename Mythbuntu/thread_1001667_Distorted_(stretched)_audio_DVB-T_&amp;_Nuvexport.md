---
title: "Distorted (stretched) audio DVB-T &amp; Nuvexport"
date: 2008-12-04
forum: Mythbuntu
---

### Post by SiHa on 2008-12-04
I've settled on Nuvexport (converting to Xvid) as my transcoder of choice, and it seemed to be working.

Until last night, I transcoded a film, and just went to check all was OK. The audio seems to be stretched to about 0.5 speed. 

This is (so far) the only reording I've noticed this on. Has anyone seen anything similar?

TIA,

Simon

---

### Post by adamish on 2008-12-19
I have noticed this a number of times recently on multiple channels in the UK using DVB-T as you are.

Have you solved this issue?

---

### Post by adamish on 2008-12-19
I've examined the audio settings of files that don't encode and those that do


One that works
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)

One that doesn't
AUDIO: 48000 Hz, 1 ch, s16le, 64.0 kbit/8.33% (ratio: 8000->96000)

---

### Post by SiHa on 2008-12-19
Ah, thanks for the info, that might help. Perhaps The audio on these needs treating differently. It makes a lot of sense as well - one of my duff ones was '633 Squadron', which is most likely single channel audio. Unfortunately, I deleted the source recording. However - it's on again over Christmas, I might record it again just to play with. 
I'll have a play with some different settings and report back.

---

### Post by SiHa on 2008-12-19
Double-post.

---

### Post by adamish on 2008-12-19
I've been messing with this for the past couple of hours, and I have a sort of fix (workaround really).

The problem appears to be to do with the format of the files. The ones that don't encode have much higher bitrates, and take much much longer.

'Good' video
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  6500.0 kbps (812.5 kbyte/s)

'Bad' video
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  15000.0 kbps (1875.0 kbyte/s)

I found that mythtranscode has a mpeg2 to mpeg2 transcode option. I tried running this on my files first, and magically it fixed the problem.

I use a wrapper script to do my transcoding (uploads to a website afterwards etc!) 

So i added the following lines before I kick off nuvexport

# fix bad files first
store=/data/film/store
mythtranscode --mpeg2 -i $store/$file -o $store/$file.transcode.mpg
mv $store/$file $store/file.old
mv $store/$file.transcode.mpg $store/$file

I also noticed that the mpeg2->mpeg2 "fixing" stage reports some problems with the stream, but moves over them okay:

mythtv@brimstone:~$ ./mythexport.sh 1001_20081218195900.mpg
Mux rate: 15.57 Mbit/s
2008-12-19 18:54:56.824 Junk in packet
2008-12-19 18:54:58.458 Junk in packet
2008-12-19 18:55:10.608 Junk in packet
2008-12-19 18:55:12.054 Junk in packet
2008-12-19 18:55:20.320 Junk in packet

---

### Post by SiHa on 2008-12-20
Great!

Thanks for that little tip. I'll wait until I have a failing recording and try it.

Cheers,

Simon

---

### Post by MisanthropicOne on 2009-01-22
Well, I have tried it (doing the mpeg2 to mpeg2 encode first that is) and have had no success. I have noticed that it only seems to do it on the recordings that have 6 channel audio though, and it seems to be stretching it out to 1/5 speed. Although some of the sound effects *may* not be affected. It's really hard to tell though and have to admit that maybe my ears are just playing a trick on me.

If I go to the system monitor and mouse over the mencoder entry while it is running, it appears to show all the comand line options that it is running, and it always says 2 channel for the audio. This is also true when using ffmpeg, but that program gives an unusable video output with all sorts of blocky chunks of color and other assorted artifacts. I thought that with either it was supposed to detect the number of audio channels and set up the encode accordingly. Could this be part of the problem, and when it downsamples it to 2 channel it's causing this horrible distortion? And if so, is it even a nuvexport issue and not a problem with mencoder itself? 

I do have a recording I have pulled from the recording directory already that I plan on trying to do manually to see if there's any difference if I tell it to encode it with 6 channel audio, but haven't taken the time to do so yet. When I do I'll be sure to post if it made a difference or not, but in the meantime, if anyone has any suggestions feel free to spout them out. I have a lot of content I want/need to export at this time, and obviously if I have to do it all by hand it's going to be one very large pain in the rear.

---

