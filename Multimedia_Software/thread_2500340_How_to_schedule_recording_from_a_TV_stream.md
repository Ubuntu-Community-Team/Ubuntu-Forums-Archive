---
title: "How to schedule recording from a TV stream?"
date: 2024-08-30
forum: Multimedia Software
---

### Post by User-007 on 2024-08-30
Okay, I have tried some ways to schedule recording from a live TV stream. I have tried streamlink with vlc and at command. My goal is to achieve a one-liner script for scheduling future stream recording and stopping recording at desired time.

My current script is
```
echo "streamlink --stdout https://yletv.akamaized.net/hls/live/622365/yletv1fin/index.m3u8 720p | tee video-$(date +'%H:%M_%m-%d-%Y').mkv | vlc - --run-time=10" | at 04:56 pm

```

Two problems persist. This makes a scheduled task, but it never starts.
Another problem is (determined by running the script without the "at" by replacing "echo" with "bash c"); the recording doesn´t stop after 10 seconds. The video window dies after 10 seconds, but recording continues..

I am not tied with VLC, if someone have better ideas to achieve my goal.

---

### Post by TheFu on 2024-08-30
So, there are lots of ways, but I use **cron** or **at** for this.

For example, the local weather is on here at 6:16pm for about 7 minutes.  So the command I use for scheduling it is

```
# tv-record.sh channel duration(min) Prog_Name
"~/bin/tv-record 11.1 7 NBC_Weather_Summary" | at 18:16
```

tv-record is a script I wrote that saves the stream from my HDHR network tuner.

In truth, I use a script to setup 'at' jobs nightly 1 week at a time.
```
$ more ~/bin/Nightly_Weather_Recording 

CMD="~/bin/tv-record.sh 11.1 7 NBC_Weather_Summary"

echo "$CMD"| at 18:16 Sun
echo "$CMD"| at 18:16 Mon
echo "$CMD"| at 18:16 Tue
echo "$CMD"| at 18:16 Wed
echo "$CMD"| at 18:16 Thu
echo "$CMD"| at 18:16 Fri
echo "$CMD"| at 18:16 Sat

```

So, if I look at the atq right now, 
```
$ atq
665     Fri Aug 30 18:16:00 2024 a tf
666     Sat Aug 31 18:16:00 2024 a tf
660     Sun Sep  1 18:16:00 2024 a tf

```
For recording OTA TV shows, I use the Jellyfin media center, which supports my HDHR tuners natively, but for the nightly weather, I don't want the entire news cast, just the weather.  Here's a blog entry that shows the tv-record script (well, the initial version) [https://blog.jdpfu.com/2016/12/13/recording-tv-from-hdhr-connect](https://blog.jdpfu.com/2016/12/13/recording-tv-from-hdhr-connect)  I have more error checking and it supports multiple tuner boxes now, but the basics are in there.

For recording internet streams, just the URL changes and I add some renaming of the output to include the source and date. Minor things for scripting.  For example, if I'm recording off Comet TV, then the URL was [https://www.comettv.com/watch-live/](https://www.comettv.com/watch-live/) back when I created that specific script.


Oh and this is VERY, VERY, important.  never try to use a GUI program with **cron** or **at**.  Just don't.

---

### Post by User-007 on 2024-08-30
Ok,  I tackled the second problem. I switched to timeout command so my command is now

```
timeout -s SIGINT 2.5m bash -c "streamlink --stdout https://yletv.akamaized.net/hls/live/622365/yletv1fin/index.m3u8 720p | tee video-$(date +'%H:%M_%m-%d-%Y').mkv | cvlc -"

```

It works.

But thing is that when I try to schedule the task with "at" command the resulting video's length is always about 5 seconds. What I do wrong? 

My command:

```
echo 'timeout -s SIGINT 2.5m streamlink --stdout https://yletv.akamaized.net/hls/live/622365/yletv1fin/index.m3u8 720p | tee video-$(date +'%H:%M_%m-%d-%Y').mkv | cvlc -' | at 09:55 pm

```

---

### Post by TheFu on 2024-08-31
Whenever using at or cron, you need to setup the scripts so that nothing is assumes. No environment variables will be there, unless they are picked up from the initial command (for at) and will never be there for a crontab.  That means, never assume the PATH is correct, so fully specify all commands. Never assume any specific PWD.  

A) **timeout** needs a full path
B) **streamlink** needs a full path
C) the output file needs a full path
D) Forget about using **VLC** or any version of it.  Just forget that tool.

When in doubt, simplify and test.  Get the command you want to be as simple as possible.
I doubt you need "bash -c". Why not just use normal bash sub-command **$( command options )** notation?  Or better, put all this into a script file so it is **echo "command-script"| at 9:55 pm**?  BTW, that leading zero on 09:55 implies AM. If you want military time, 21:55 is the time. Computers don't like to ambiguous inputs.  09:55 PM is ambiguous.  Either 21:55 or 9:55 will do.

---

### Post by User-007 on 2024-08-31
Thank you, TheFu. I noticed already after your first post the advice not to use gui programs with "at". So I eventually solved also my second problem by excludiong the "vlc" from the command. Sorry for forgetting to answer then.

So I ended up with two different commands. First one is to schedule saving a future video stream whereas the second one just starts the recording immediately. {LENGHT}, {URL} and {DESIREDTIME} must be replaced values by user. "At" and "streamlink" must be installed, both are found in the repos.

```
echo 'timeout -s SIGINT {LENGTH} streamlink --stdout {URL} 720p | tee video-$(date +'%H:%M_%m-%d-%Y').mkv' | at {DESIREDTIME}
```


```
timeout -s SIGINT {LENGTH} bash -c "streamlink --stdout {URL} 720p | tee video-$(date +'%H:%M_%m-%d-%Y').mkv | cvlc -"
```


My goal was to achieve those commands, because I think there is no GUI for that and it is easier to modify the commands rather than script files.

---

### Post by TheFu on 2024-08-31
I've never used **streamlink**.  It is easier than **yt-dlp**?
I played with it in 2022 and found it overly complex for what it does. The x-discontinuity flag in streams is still a problem to my knowledge.  I tried to get streamlink working then to solve the issue and failed.  Perhaps I should try again.

---

### Post by User-007 on 2024-08-31
I haven't used yt-dlp so I have no contribution.

---

### Post by TheFu on 2024-08-31
> **User-007 said:**
> I haven't used yt-dlp so I have no contribution.

Wow!  **yt-dlp** is **THE** downloader for videos.  It will discover the stream in most URLs to grab.  Great for Tubi and other streaming sites, like youtube, obviously.  Just be certain to get the version from [https://github.com/yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) - it has a self-update feature that I run with my weekly ubuntu patching on desktop systems.  I've used it with NBC, ABC, Hulu and a few others too.  DRM does get in the way sometimes, but not always.  Getting captions/subtitles is one of the features I love.

---

### Post by User-007 on 2024-08-31
> **TheFu said:**
> Wow!  **yt-dlp** is **THE** downloader for videos.  It will discover the stream in most URLs to grab.  Great for Tubi and other streaming sites, like youtube, obviously.  Just be certain to get the version from [https://github.com/yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp) - it has a self-update feature that I run with my weekly ubuntu patching on desktop systems.  I've used it with NBC, ABC, Hulu and a few others too.  DRM does get in the way sometimes, but not always.  Getting captions/subtitles is one of the features I love.

Thanks for pointing out this app. Yt-dlp seems to simplify the commands a lot. Already ready to use for future scheduling with "at". But, when I decide to start recording immediately, how to open a video simultaneously?

---

### Post by TheFu on 2024-09-01
> **User-007 said:**
> Thanks for pointing out this app. Yt-dlp seems to simplify the commands a lot. Already ready to use for future scheduling with "at". But, when I decide to start recording immediately, how to open a video simultaneously?

That isn't what yt-dlp does.  It generally gets the captions, then the video, then the audio tracks.  Those are separate and in order, not muxed together until after all are already local.

If you want a way to watch and save, **mpv** has that with a little configuration.  Works with many IPTV streams, but not all of them.  A few friends use that, but I don't.  Heck, I don't even watch live sports anymore.  I wait till it is over then remove all the commercials and transcode from mpeg2 --> h.264 before watching.  Just started doing that process with the UCLA-Hawaii game that just finished.  Not really my teams, but the first of any interest this season, so I decided to test my processing before my team is on TV next Saturday.  ;)

The command options have changed I think, but something like this:
```

$ mpv --record-file=video.mkv https://www.youtube.com/watch?v=…

```
I think the --record-file is deprecated now.  **mpv** uses either **yt-dlp** or **youtube-dl** to get the stream.  They just need to be installed and in your PATH to work.  yt-dlp is better maintained and has more features, but the current features map 1-to-1 to the youtube-dl options, so they are interchangeable for the most part.

Ah ... in the  mpv manpage, 
```
       --stream-dump=<destination-filename>
              Instead  of playing a file, read its byte stream and write it to the given destination file.
              The destination is overwritten. Can be useful to test network-related behavior.
```

BTW,  a script is just like a command, just saved to a file. Scripts don't need to be complex programs.  They can be 1 or 2 lines that you would have typed in previously, but if you are doing that more than twice, create a script to avoid that typing or forgetting options.  I don't remember lots of options to many different commands, but I have about 1000 little scripts that do so I don't need to remember those details.

---

### Post by User-007 on 2024-09-01
Seems that easiest way to record and view simultaneously is to use ffmpeg.

```
ffmpeg -i {URL} -codec:a aac -b:a 192k -codec:v copy -f mpegts - | tee >(ffplay -f mpegts -i -) | ffmpeg -y -f mpegts -i - -c copy output_$(date +%Y%m%d%H%M%S).mp4
```

This command is far from natty but it seems to work.

---

