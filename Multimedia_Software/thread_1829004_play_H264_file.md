---
title: "play H264 file ?"
date: 2011-08-20
forum: Multimedia Software
---

### Post by ieee488 on 2011-08-20
I downloaded a file from Youtube as a mp4.

Used ffmpeg to demux into an audio file *.aac and a video file *.h264

Is there a program that can play the H264 file?

I tried VLC, but no video.

---

### Post by BicyclerBoy on 2011-08-20
GPIB/HPIB..
VLC MythTV has played this video codecs for > 3 yrs..

You must have some packages missing, but I did think VLC was self-contained..

Try adding medibuntu repository & adding the un-stripped extras libav* (ffmpeg) packages (7) & non-free codecs.
[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

Does your PC have enough grunt to play it ?

---

### Post by ieee488 on 2011-08-20
> **BicyclerBoy said:**
> 

Does your PC have enough grunt to play it ?
It should. It is a Core 2 Duo.
I can play the mp4 just fine.



> **BicyclerBoy said:**
> 

adding the un-stripped extras libav* (ffmpeg) packages (7) & non-free codecs.


Can you explain what this means?

---

### Post by SeijiSensei on 2011-08-20
Just install **smplayer**, and you'll be fine.

---

### Post by ieee488 on 2011-08-20
It doesn't look like the H264 file is valid.

I followed the directions at [http://gordonazmo.wordpress.com/2010/03/17/demuxing-and-re-muxing-m2tsmp4flv-to-mkv-under/](http://gordonazmo.wordpress.com/2010/03/17/demuxing-and-re-muxing-m2tsmp4flv-to-mkv-under/)

Not sure what I have to do to get a valid H264 file.

---

### Post by BicyclerBoy on 2011-08-20
Sorry misunderstood..

You are trying to play the H264 demuxed stream  raw dat file..
This output stream has no container & I think it is not playable..except by some muxing tools maybe...

You have to remux into a container like mkv.
You can have no audio stream by using a null audio input stream.

Media files are containers with multiple (muxed - multiplexed) streams of packetised data.
The streams can not be used directly without container.
Many containers have limited codec type support.
Some containers are designed to be able to be started at any point/time/place (mpeg4-ts).

---

### Post by ieee488 on 2011-08-20
My ultimate goal is to edit out some of the 3 minute video while at the same time replacing some of the audio. Purely as a learning experience.
So I thought demuxing and then editing each of the separate streams would be the best approach.

Now, I am thinking I'll first edit the mp4 file concentrating on just the video. Then after I have a new mp4 file, demux it. Edit the *.aac audio file, and then mux the H264 and AAC streams back together again.

---

### Post by BicyclerBoy on 2011-08-20
Each packet PES has timestamp info that is linked into the container timing info.

Chopping & joining pieces requires this stuff to be fixed up else you get glitches on the transitions, A/V sync problems or worse.

You can edit the individual streams & remux but I not sure how to deal with changing the duration of the streams.
You may need to cut the original file into the required segments & then deal to each separately. This is what a video editor does.
You can then join the separate video files with ffmpeg, it will fix the timing info (I believe).

---

