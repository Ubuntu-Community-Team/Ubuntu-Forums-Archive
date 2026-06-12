---
title: "How can I Create Video for upload to Google video from a DVD"
date: 2007-07-13
forum: Multimedia Production
---

### Post by sefs on 2007-07-13
Can someone write a HOWTO for this? :)

Requirements for video on Google Video are

NTSC (4:3) size and framerate, deinterlaced
Video Codec: MPEG2 or MPEG4 (MPEG4 preferred)
Video Bitrate: at least 260Kbps (750kbps preferred)
Audio Codec: MP3 vbr
Audio Bitrate: at least 70Kbps (128 Kbps preferred) 

I can rip the DVD into one vob file that contains both video and audio by using the command ...

```

mplayer dvd://1 -dumpstream -dumpfile rippeddvd.vob

```

This generates a file approximately 4.1 GB in size.

After that i am stuck.  Basically from this file I want to re-encode it to meet Google Video's requirements, I would also like to get it to be below 100 Megabytes if possible :)

Thanks.

---

### Post by jacob01 on 2007-07-15
if you want it to be under 100 meg then try to convert it using vlc media player located in the repositorys 

once vlc is installed
 you open up vlc and load a vid
then go to file wizard
transcod/save file
next
mark existing playlist item
next
mark transcode video and audio and chouse a bitrate so that it is under 100 meg you might have to play around with the bitrate a bit to get it to the size you want
next
chouse the encapulation format
next
chose file and finish

it will be hard to get a 4 gig file under a hundred meg 
you are going to loose a lot of quality 
 a suggestion is to use a program like avidmux or some other simple video editor and cut the video into smaller pieces to upload to google

hope this helps

---

