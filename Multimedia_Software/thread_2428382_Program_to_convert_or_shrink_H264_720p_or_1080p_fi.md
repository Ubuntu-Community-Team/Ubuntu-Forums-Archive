---
title: "Program to convert or shrink H264 720p or 1080p file to DVD5 (4,3 GB) size."
date: 2019-10-03
forum: Multimedia Software
---

### Post by jasper99 on 2019-10-03
Program to convert or shrink H264 720p or 1080p file to DVD5 (4,3 GB) size in H264.
Or can set a target size.

At HandBrake don't can set a target size.

---

### Post by uRock on 2019-10-03
Are you trying to rip DVDs or create them? To create DVD images I use Devede, which is in the software center. Ripping is a touchy subject here, as it usually violates one law or another.

---

### Post by SeijiSensei on 2019-10-03
You can do that with ffmpeg: [https://stackoverflow.com/questions/29082422/ffmpeg-video-compression-specific-file-size](https://stackoverflow.com/questions/29082422/ffmpeg-video-compression-specific-file-size)

---

### Post by jasper99 on 2019-10-03
> **uRock said:**
> Are you trying to rip DVDs or create them? To create DVD images I use Devede, which is in the software center. Ripping is a touchy subject here, as it usually violates one law or another.

No, i want to shrink a recorded 720p H264 file of 8-9 GB to 4,3 GB DVD size in 720p H264.

> **SeijiSensei said:**
> You can do that with ffmpeg: [https://stackoverflow.com/questions/29082422/ffmpeg-video-compression-specific-file-size](https://stackoverflow.com/questions/29082422/ffmpeg-video-compression-specific-file-size)

Here i must calculate, i want to set a target size only. As Wondershare Uniconverter (Windows)

---

### Post by uRock on 2019-10-03
I haven't tried it, but Openshot may be able to do that for you.

---

### Post by jasper99 on 2019-10-04
Can anyone run and use [COLOR=#000000]Wondershare Uniconverter (Windows version) trough Wine?

I have tried, but at me that don't working.[/COLOR]

---

### Post by TheFu on 2019-10-04
Don't know if this will help in anyway at all, but ... 

I transcode videos all the time.  For me, size is the least important issue because a 2 hour video at 720p in h.264 will easily be under 2GB in size without any visual artifacts.  Why create a larger video just to fill a DVD when it isn't needed?

I have a hardware video recording device that makes h.264/aac/mp4 videos.  This device is mostly concerned about being fast and getting the video to storage. Compression is of little concern.  I take the 10G-15G video the device made and run it through handbrakeCLI to get a 1-3G file.  It is about 1GB for each hour at 720p in an h.264/aac/vobis/mkv file.  I add a vorbis audio track since some of my players don't like the AAC audio initially created.

I'm certain that ffmpeg could accomplish the same thing, but I haven't bothered trying to find all the desired options to make it as size efficient as handbrake is out of the box.  

Again, my goal is to have zero artifacts in the file video, but the only way that 1 file would need to be 4.3GB in size were for 4+ hrs of action video that wasn't sports.  For most sports, the compression is really efficient since the playing field is consistent.

---

### Post by jasper99 on 2019-10-05
I have found that DevedeNG can convert to Matroska/H264 with DVD5 (4,3GB) or DVD9 (7.95 GB) sizes

---

