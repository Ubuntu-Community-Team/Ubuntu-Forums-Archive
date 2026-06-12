---
title: "Capturing/recording v4l2-input (camera, EasyCap...) to file with FFmpeg"
date: 2017-03-05
forum: Multimedia Software
---

### Post by xinuzi on 2017-03-05
Hello,

First, install a decent FFmpeg version. Details: elsewhere (see some comments further).
Most systems will have it by default.

Second, don't complicate things too much. FFmpeg coding is not easy. Don't overdo it.

**1. PREPARATION:**

**1.1 SET SOUND INPUT DEVICE**

Set analogue input device usb hub TV etc (if it concerns a tv to usb input) in your sound settings.

**1.2 CHECK VIDEO AND AUDIO INPUT - SEVERAL POSSIBILITIES**

'sudo apt-get install v4l-utils' and use the command 'v4l2-ctl --list-devices' to check video input,

and/or:

VLC, Media record, select video (e.g. /dev/video0) and sound (e.g. hw:1,0) under 'Video Camera' for the correct TV system (e.g. PAL) and test/play the result.

and/or:

Check audio with the command 'arecord -l' (most important).

[B]2. CAPTURE/RECORD

[/B]These are some codes that work for me on several systems (older and newer) and this after several try-outs.
Input: **EasyCap stick** (tv/recorder-scart-OUT-composite-EasyCap-long-usb-or-composite-or-s-video-cable-to-usb-port-laptop / PAL TV).

Paste the given code line in your terminal.
Interrupt/save with 'q'.
Reinsert with 'Arrow Up'.
Posssibly change the file number or name in case of new file.

The first take will often give a '0 fps' message in your terminal. This disappears from the second take. 
No picture or no sound often means you're not using the right video4linux or alsa number (See: PREPARATION.)

[B]2.1 MPEG4-PART10 (H264, X264)

[/B]```
ffmpeg -f v4l2 -standard PAL -thread_queue_size 512 -i /dev/video0 -f alsa -thread_queue_size 512 -i hw:0,0 -vcodec libx264 -preset superfast -crf 25 -s 640x480 -r 25 -aspect 16:9 -acodec libmp3lame -b:a 128k -channels 2 -ar 48000 out_0001.mkv

```

The v4l2 'standard' is important for the right picture scaling. PAL (Europe) or NTSC (U.S. = v4l Default) or SECAM (France) most often.

mp4-outputcontainer can be used as well of course (Eventhough, '.mkv' = more 'flexible').
Best preset: 'superfast' seems to work in most cases. Otherwise: 'veryfast'. In case of bad, stuttering reception: 'ultrafast' (but, less quality/less compression).
All the possibilities: ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow, placebo.

I've used mp3lame after aac started stuttering. Most used values: 44100 or 48000 hz. I try to keep the original hz audio frequency of the input as much as possible. Of course keeping the original input audio with '-acodec copy' is also an option. Recoding the audio afterwards doesn't take too much time.

'**-thread_queue_size n**': when placed twice, after 'v4l2' and after 'alsa' (whatever the used codec), it deals with the possible repeatedly occurring message '**ALSA buffer x-run**' and bad sound recording. After doing this the message appeared once, on an older system, then disappeared with a smooth recording of audio as a result. Common settings: 512, 1024, 2048.

'**-crf**': best quality-filesize results between 20 and 28.

[B]2.2 MPEG4-PART2 (H263, XVID)

[/B]I prefer this codec (sorry! - whatever 'they' say) as video cutting afterwards, with ffmpeg or more easily with avidemux, works better than in case of mpeg4-part10.
'mpeg4' or 'mpeg4 -vtag xvid' or 'libxvid' (the last one sometimes gives message of not present library. Just 'mpeg4' is maybe the safest.).

[B]2.2.1 Constant bitrate
[/B]
```

ffmpeg -f v4l2 -standard PAL -thread_queue_size 512 -i /dev/video0 -f alsa -thread_queue_size 512 -i hw:0,0 -vcodec mpeg4 -b:v 1800k -s 640x480 -r 25 -aspect 16:9 -acodec libmp3lame -b:a 128k -channels 2 -ar 48000 out_0001.mkv

```

[B]2.2.2 Variable bitrate
[/B]
```

ffmpeg -f v4l2 -standard PAL -thread_queue_size 512 -i /dev/video0 -f alsa -thread_queue_size 512 -i hw:0,0 -vcodec mpeg4 -q:v 4 -s 640x480 -r 25 -aspect 16:9 -acodec libmp3lame -q:a 7 -channels 2 out_0001.mkv

```

Bitrate or qscale = personal choice (see documentation). Variable bitrate should give slightly better quality but it sometimes 'fluctuates' ('bitrate jumps') so much that you get uncertain file size and quality.
Other settings: see [FFmpeg Documentation]("https://www.ffmpeg.org/documentation.html").

No video - audio syncproblems with above codes.

It can be challenging to try to avoid sudden black frames. Especially in longer recordings.
This is stronly dependent on the hardware state at the moment of capturing.


[COLOR=#ff0000]
[/COLOR]

---

### Post by opsusec on 2017-03-06
> **xinuzi said:**
> Hello,


First, install a decent FFmpeg version. Details: elsewhere.
Most systems will have it by default.


Second, don't complicate things too much. FFmpeg coding is not easy (and I'm not an expert myself). But it works very well once you get it right.


Maybe these codelines help you in what you want to do...


**1) Capture/record video + audio, well-synchronised to file**


I often get the impression, in this context, that capturing to xvid/mp3/avi gives better results than e.g. x264/aac/mp4.
Or, you could try xvid+mp3 (a very good match indeed - whatever modern companies want to force upon you these days - if, only, ogg vorbis could be as popular + functional...) in the flexible mkv container...
Just test out.


The code (for, in the presented case, recording from a PAL tv system from scart OUT over composite cable to usb with EasyCap stick in between):


```
ffmpeg -f v4l2 -i /dev/video0 -f alsa -i hw:2,0 -vcodec libxvid -b:v 1700k -s 720x576 -r 25 -aspect 16:9 -force_key_frames 00:00:00.000 -acodec mp3 -b:a 128k -channels 2 -ar 44100 output.avi

```

-b:v = video bitrate kbps
-s = size widthxheight (chosen the same as the input here)
-r = fps or frames per second. Usually 25 with PAL, rather 30 with NTSC.
-aspect = DAR (Display Aspect Ratio). 16:9 for a more modern widescreen HD look.
-force_key_frames 00:00:00.000 = for some reason very important concerning video and audio synchronisation.
-b:a = audio bitrate. Most commonly used are 96 or 128 kbps.
-channels 2 = stereo mode.
-ar = sound frequency (most often: 44100 Hz, or 48000 Hz.)


The most logical way for me is to first group the input video and audio streams (as-they-are - without too much extra coding),
then write the file details of video and audio (-vcodec and -acodec).


'/dev/video0' and 'hw:2,0' are system dependent.
You could open VLC -> Media -> Recording device -> Device selection -> Video camera (or sth of the sort) and then check the available Video and Audio devices and select especially the Audio device that gives sound. E.g.: hw:1,0 or hw:1,2 or hw:2,0 or other.
(I would use VLC rather for viewing than for recording/Converting/Saving to a certain codec.)


You paste the above codeline (presumably from a text file) in your terminal (which you probably open from the dir where you want the video file to be saved).
Recording can be interrupted/saved by pushing 'q'.
Reinserted by using the upper arrowkey. Possibly change the output filename or its file number in case of new file.


If you would still experience video-audio sync problems, use this:


**2) Synchronise video with audio afterwards**


```
ffmpeg -i input.avi -itsoffset 0.2 -i input.avi -map 0:0 -map 1:1  -acodec copy -vcodec copy synced.avi

```

wherest '0.2' is the delay in seconds. Most often '0.2', sometimes '1.0' in very badly synced videos.


This codeline can also come in handy if you want to edit the video afterwards in avidemux e.g. (even if you don't hear anything, it will be there)
Even if you use -itsoffset 0.0 .


If you want another aspect ratio for your video, use this:


**3) Change Display Aspect Ratio in stream copy mode**


```
ffmpeg -i input.avi -vcodec copy -acodec copy -aspect 4:3 output.avi

```

Most of the time you will want the video to change from 4:3 to 16:9 though.


These ffmpeg codes work for me for the moment, but you may of course always comment if you see sth wrong.


do you think there would be a way to use this to audit remote systems internally, thus recording your own logs to assess?

Kudos and +1 for the info

---

### Post by xinuzi on 2017-03-06
No idea opsusec.

(Changed a few things in my original post btw)

> **xinuzi said:**
> 
First, install a decent FFmpeg version. Details: elsewhere.
 Most systems will have it by default.


These installation instructions should work for most for the moment:

```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install ffmpeg
```

as described here:

[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

I'm sorry for reediting this post all of the time,
but, things evolve as I'm testing.

---

### Post by xinuzi on 2017-04-05
(Cut - See first post.)

---

### Post by xinuzi on 2017-04-14
[COLOR=#000000](Cut - See first post.)[/COLOR]

---

