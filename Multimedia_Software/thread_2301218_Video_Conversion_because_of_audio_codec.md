---
title: "Video Conversion because of audio codec"
date: 2015-10-31
forum: Multimedia Software
---

### Post by FreakShow! on 2015-10-31
Hi all,

I spent a time converting all my DVDs to be video files on a home server. All has been going great for ages until now that I have a tablet and want to watch things on there. Unfortunately, the options I used was to create an AVI files with the AC3 audio codec, and pretty much all the apps I used to use have stopped supporting the AC3 codec for free.

So what is the easiest way of running a command-line to convert all videos, keeping the video stream the same, just processing the audio to convert to a better (freely supported) codec. Some of the videos are in different formats, so hopefully I'll be able to just copy the stream and so there won't be a forced setting of the output resolution and framerate, just copy the input video.

I hope this is the right place to ask!

I know it'll take a long time, but the server is on 24/7 and can quietly work it's way through the folders.

---

### Post by TheFu on 2015-10-31
Don't bother.

Setup Plex Media Server and it will transcode on-the-fly to a codec required for each device, as needed, only when needed.

After all, in 5 more years there will be new video and audio codecs that devices today don't support. Every conversion introduces more "error" in the resulting output.

However, if you must ....   ffmpeg or avconv can do this.  One way:

```
#!/bin/sh
FF_OPTS="-vcodec copy -c:a aac"
nice ffmpeg -y -i "$@" $FF_OPTS  "$@.mkv"
```

This is a very simplistic method and the ffmpeg available in the ubuntu repos is very out of date, so it may be desired to use a reputable PPA version.  avconv can probably do it too. ffmpeg and avconv are both amazing tools.  There are others like mencoder too.

Pretty much **every** other tool out there is based on the ffmpeg or mecoder tools, regardless of platform.

OR

You can use a tool like handbrake with the DVDs to create h.264+AC3+AAC+subs+SRT videos in MKV containers.  Thats 1 video track, with as many audio tracks and subtitle tracks as you like.  On a modern CPU,  each transcoding job takes about 10-20 min.  I put the source AC3 audio into the resulting container with all available audio tracks and all subtitles.  Also, I'll transcode the primary  5.1 English into AAC 5.1 audio and include it ....  Roku and Chromecast require AAC audio.  Meh.  

A few  years ago, I had a similar issue.  Was using XBMC (now Kodi), then learned about PlexMS...  never looked back. I DO NOT have a  plex account and DO NOT allow that system to contact any plex servers.  Not needed if you only want LAN access and  for WAN stuff access a full VPN that extends the subnet to your remote devices works.

Anyway, hope this helps with your decision.

---

### Post by FakeOutdoorsman on 2015-10-31
What audio and container formats do you want? What does the tablet support?

---

