---
title: "Any good substitute for Cheese?"
date: 2020-10-29
forum: Multimedia Software
---

### Post by la.khan on 2020-10-29
Hello all,

I use Cheese application that comes installed with Ubuntu Linux 20.04 to access my web cam. This application has no configuration settings and records video only in .webm format. Is there a good application that can record video feed from web cam in other formats (ex. MP4)?

I looked around the web and found webcamoid ([https://webcamoid.github.io/)]("https://webcamoid.github.io/"). While this application claims to record in multiple formats (including MP4), this might be an overkill, with all the bells & whistles. Is there a better alternative to Cheese application? Something simple to use.

Appreciate any pointers/insights in this regard. Thanks!

---

### Post by &amp;KyT$0P# on 2020-10-29
guvcview?  It's in the normal Ubuntu repositories.

---

### Post by SeijiSensei on 2020-10-29
Repackaging into MP4:

```
ffmpeg -i /path/to/original-video.webm -acodec copy -vcodec copy new-version.mp4
```

The -acodec and -vcodec parameters may not be necessary.

---

### Post by ajgreeny on 2020-10-29
You can also use vlc if you already have it installed.
Go to Media ->Open Capture Device, use **Video Camera** in the **Capture Mode** drop down, then select the device in **Video Device name**.
I have two devices to choose from only one of which is active, /dev/video0, and it saves as an .avi by default.

---

### Post by MartyBuntu on 2020-10-29
Agree with VLC and guvcview.

---

### Post by la.khan on 2020-10-29
Thanks for the replies.

I looked up guvcview and it is simple  enough for my purpose. I installed it from Ubuntu software and has  enough options for me to play around with the output. However, I  couldn't find a way to save my file to MP4 format. Video files are saved  saved either as mkv, webm or avi. There is no option to save a file in  MP4 format.

The default video codec guvcview uses is MPEG4-ASP. I  have tried other video codes too (MPEG4-AVC, MPEG video1, HEVC H265   etc) but none of these video codecs have an option to save my file to  MP4 format.

Is there a plugin I need to install?

---

### Post by ajgreeny on 2020-10-30
Why is saving as mp4 so important?  I use mkv generally as it produces smaller files which are more universally  playable.
Do you need mp4 for a particular player?

---

### Post by la.khan on 2020-10-30
> **ajgreeny said:**
> Why is saving as mp4 so important?  I use mkv generally as it produces smaller files which are more universally  playable.
Do you need mp4 for a particular player?
I don't have a particular player in mind. For video, I thought MP4 was the most widely used format. Is that a misconception? If I share an MKV file, can a MP4 player play it? If yes, my problem is solved.

---

### Post by TheFu on 2020-10-30
mp4, webm, mkv, avi are just "containers". Some are restrictive about the things they can hold i.e. the video, audio, and other tracks.

MKV is the most generic of the containers. Any vdeo/audo/text/subtitle/caption formats from any non-proprietary format can be stored inside mkv. 

webm is a highly restricted version of mkv, created by Google so they could force their vp8/vp9 codecs onto the world.

mp4 is a little old-school these days. I can think of 1 way where mp4 is better, sometimes, than mkv.  I can think of 20 ways that mkv is better than all other containers.

Converting any other format into mkv container is easy using ffmpeg or mkvmerge. tools. This process is as fast as a file copy and does NOT involve any transcoding or change in the quality of the video or audio.

```
mkvmerge -o output.mkv  input.mp4
```

mkvmerge has all sorts of capabilities, like merging multiple videos into a single video file or splitting videos apart including the audio, srts,subs, across all tracks - without transcoding! This can be extremely useful.

As long as the video codec used is h.264 and the audio codec is aac or vorbis or both, then it shouldn't matter what container is used.    If the player is newer, then vp8 or vp9 or h.265 can be used for the video.  Web browsers all seem to support webm (vp8/vp9 + ogg/vorbis). Those codecs have all been released as patent-free.  Honestly, they are all pretty great if our players aren't too old.
vp8 --> h.264 (approx.)
vp9 --> h.265 (approx.)
I've been using multichannel vorbis for audio files for a few years by choice for compressed audio. Not all players support it but android does.
People with Apple hardware should check compatibility.  I don't have any recent experience with anything from apple.

 guvcview is ok for simple needs. Sometimes we all get to the point that OBS is required.

---

### Post by SeijiSensei on 2020-10-30
Lately I've been editing Zoom streams for public access using KDEnlive and have been saving to WebM rather than MP4. These files are distributed over the web, though, so they are viewed in a browser, not a video application. Still, mpv has no problem playing a video in WebM either. They also play on my Android phone using MXPlayer.

---

### Post by la.khan on 2020-10-30
TheFu: That was informative. Thanks, appreciate it.

I guess that resolves my problem!

---

