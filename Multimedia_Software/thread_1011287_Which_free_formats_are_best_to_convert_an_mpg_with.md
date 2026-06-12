---
title: "Which free formats are best to convert an mpg with?"
date: 2008-12-14
forum: Multimedia Software
---

### Post by phenest on 2008-12-14
I have a high quality mpg that I want to convert to a free format such as theora. I could use ffmpeg2theora or OggConvert but I noticed that xVid4 has much better quality and smaller file sizes. I've noticed that most videos that use xVid have used mp3 for the audio and avi as the container, but mp3 is hardly free. So I tried vorbis and used an ogg container but the first 2 or so seconds of the video is corrupt which doesn't happen if I use mp3.

So... am I doing something wrong with xVid and vorbis? Or is there a better way?

I'm using AviDemux but can't figure this out.

EDIT: The audio in the mpg is ac3. Could I use that?

---

### Post by phenest on 2009-01-10
After much encoding and playback with various encoders for both video and audio, I'd like to share my results.

The test video was ripped from a DVD: Red Dwarf Series 1 Episode 1 - "The End". I used mplayer to rip to a basic MPEG-2 which was 1GB in size for a 30 minute video.
```
mplayer dvd://3 -dumpstream -dumpfile rd1-1.mpg
```
For comparison purposes, all video and audio was converted using identical variable bitrates each time. Video was at the rate of 250k, and audio at 64k. You may think this is a pretty low video bitrate, but if you compare the different codecs visually, you'll see why.

First up, is Theora. For this I used ffmpeg2theora. I could have used OggConvert and ended up with the same results.
```
ffmpeg2theora rd1-1.mpg -V 250 -A 64 --optimize --deinterlace -o rd1-1.ogv
```
Awful! Just awful! Lots of flickering and pixelation. Very low quality and a file size of 114.5MB.

Next is xVid. For this I used Avidemux. Configure the codec to Single Pass Variable Bitrate and choose 250 for the bitrate. Set the Audio codec to MP3 and set the Bitrate to 64. Set the container to AVI and save. Much better. A lot less pixelation and much easier on the eyes. Still low quality though, but the file size was only 71.8MB. Because of the smaller file size, it would have been possible to increase the video bitrate.

And last is x264. I used Avidemux again. Configure the video bitrate to 250. Choose AAC for audio and set bitrate to 64. Use the AVI container and save. Fantastic quality! The same quality settings as the previous 2, and yet significantly better visually. File size is practically the same as xVid.

But here's the interesting bit. The x264 codec is the free version of h264, that is, it's released under the GNU GPL, whereas h264 has patents applied. Also, the AAC audio codec is also free of patents. So this is now my codecs of choice for videos.

---

