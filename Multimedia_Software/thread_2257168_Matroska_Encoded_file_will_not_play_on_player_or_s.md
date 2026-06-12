---
title: "Matroska Encoded file will not play on player or stream to Chromecast"
date: 2014-12-17
forum: Multimedia Software
---

### Post by laserman on 2014-12-17
I learned about Screencasting from this post:

[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

Using instructions posted on the first page, I was successful in capturing a lossless video streaming on a web page and playing it back in xine.

```
ffmpeg -f alsa -ac2 -i pulse -f x11grab -r 30 -s 852x464 -i :0.0+533,434+nomouse -c:a libfdk_aac -b:a 192k -vcodec libx264 -preset ultrafast -crf 0 -threads 0 testingoutput.mkv
```

After playing it in xine, I noticed a delay in the audio. Seemed a lot of other people had similar problems with this too. At the end of the same post, on page 25, I noticed another user posted a fix of changing the framerate from -r to -framerate. That seemed to fix the audio delay. 

```
ffmpeg -f alsa -ac2 -i pulse -f x11grab -framerate 30 -s 852x464 -i :0.0+533,434+nomouse -c:a libfdk_aac -b:a 192k -vcodec libx264 -preset ultrafast -crf 0 -threads 0 testingoutput.mkv
```

I still have not been able to figure out the video not being played on other devices. I can even play it on VLC but the video still has problems and the player doesn't seem to like the stream. I've used Audials to record the same video at another time and have not had any issues in streaming to my TV or playing the video on other platforms (PC or Android tablet). Problem with Audials is, it is very labor intensive on the computer whereas I do not see the burden on the computer using FFmpeg. I've also tried to view the mediainfo but am not versed enough to tell what I need to change in the string in order to make the video viewable across other platforms. I have several mediainfo files I can provide as needed. I have even converted the file from .mkv to mp4 to no avail, getting the same problem with the movie player, stating that it is unable to play the video.

One other platform I've used is Handbrake. I've been successful ripping a DVD and converting it to Matroska and streaming it to the TV with no issues whatsoever.

This version of FFmpeg has just been compiled a couple of days ago from the instructions posted on [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)

laserman

---

### Post by FakeOutdoorsman on 2014-12-17
Devices are picky. Once you're done encoding the screencast you can try re-encoding the resulting lossless output to something that will be more compatible:

```
ffmpeg -i lossless.mkv -c:v libx264 -crf 20 -pix_fmt yuv420p -c:a copy output.mkv
```

Other things to try:
[list]
[*]If the device doesn't like MKV, use MP4.
[*]The device may require a certain profile, such as "-profile:v baseline" or "-profile:v main".
[*]You may be able to screencast directly to the lossy, more compatible version and skip the lossles step. However, it will be more CPU intensive (hence the two step process).
[/list]

---

### Post by laserman on 2014-12-18
> 
```
ffmpeg -i lossless.mkv -c:v libx264 -crf 20 -pix_fmt yuv420p -c:a copy output.mkv
```



Yes, this corrected the streaming issue to any and all the devices I was trying.

Now, I have a hint of a delay with the audio. Looks like that was there on the original capture. Seems to be regular across the recording, just a bit noticeable but better than before. I'll try adjusting the FPS and see if that changes anything, unless there are other options?

laserman

---

### Post by FakeOutdoorsman on 2014-12-19
Perhaps use -c:a copy in your lossless encoding, then in your second step re-encode with libfdk_aac.

Or run two ffmpeg commands: one for video and one for audio. Then remux them.

```
ffmpeg -f x11grab -framerate 30 -video_size 852x464 -i :0.0+533,434+nomouse -vcodec libx264 -preset ultrafast -crf 0 video.mkv & \
ffmpeg -f alsa -ac 2 -i pulse -c:a copy audio.mka
ffmpeg -i video.mkv -i audio.mka -c copy -shortest output.mkv
```

That might not work well though if the two devices don't initialize at the same time. Just an idea that I've never tested.

Or re-compile with --enable-libpulse for [PulseAudio input device](https://ffmpeg.org/ffmpeg-devices.html#pulse) support and try that instead of ALSA. You'll need libpulse-dev as a dependency before compiling ffmpeg.

As for fixing the existing video you can maybe try the [adelay](https://ffmpeg.org/ffmpeg-filters.html#adelay) filter (I've never tried it and didn't read the docs).

---

### Post by laserman on 2014-12-19
> **FakeOutdoorsman said:**
> Perhaps use -c:a copy in your lossless encoding, then in your second step re-encode with libfdk_aac.

I will give that a try. I did try the change in FPS to 29.97 and the audio is spot on. I like the option above too. Will have to try that and see how it works out with the -framerate 30.

> **FakeOutdoorsman said:**
> Or run two ffmpeg commands: one for video and one for audio. Then remux them.

```
ffmpeg -f x11grab -framerate 30 -video_size 852x464 -i :0.0+533,434+nomouse -vcodec libx264 -preset ultrafast -crf 0 video.mkv & \
ffmpeg -f alsa -ac 2 -i pulse -c:a copy audio.mka
ffmpeg -i video.mkv -i audio.mka -c copy -shortest output.mkv
```

That might not work well though if the two devices don't initialize at the same time. Just an idea that I've never tested.

True, that might be tricky.

> **FakeOutdoorsman said:**
> Or re-compile with --enable-libpulse for [PulseAudio input device]("https://ffmpeg.org/ffmpeg-devices.html#pulse") support and try that instead of ALSA. You'll need libpulse-dev as a dependency before compiling ffmpeg.

I had wondered about taking another stab at the audio, still learning and I will try this one.

> **FakeOutdoorsman said:**
> As for fixing the existing video you can maybe try the [adelay]("https://ffmpeg.org/ffmpeg-filters.html#adelay") filter (I've never tried it and didn't read the docs).

This'll be a testing process for sure. I would like to try it but it will be after Christmas.

Thanks for the inputs and I will report back with what I find out.

---

### Post by laserman on 2015-03-02
FakeOutdoorsman, I wanted to follow up with this, continuing to use the initial command, I found that the delay in audio was the result of Chrome. I used Firefox and had no delay, whatsoever. I don't know the specifics on how Chrome handles the audio or translation of the video with audio but there is clearly a .5 to .7 second delay in the audio using Chrome. I haven't had the need to use any of the other commands to split the audio and resplice. Have you heard of anyone else experiencing this with Chrome?

laserman

---

### Post by FakeOutdoorsman on 2015-03-02
Sorry, but I haven't heard of that issue before, and I'm not a Chrome user or very knowledgeable in various browser playback issues.

I suppose you'll just have to keep experimenting. Not a very helpful reply...

---

### Post by mc4man on 2015-03-03
No clue about chrome but - 
did notice here that vlc has an issue with a screen cap using  pcm_s16le (copy), @ 48k. (- other players are fine..
so for heck of it maybe try  - 
-c:a pcm_s16le -ar 44100

---

