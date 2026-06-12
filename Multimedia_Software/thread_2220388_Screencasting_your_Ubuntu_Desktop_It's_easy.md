---
title: "Screencasting your Ubuntu Desktop: It's easy"
date: 2014-04-27
forum: Multimedia Software
---

### Post by patrickballeux on 2014-04-27
Hi fellow friends...

I've always been interested in audio and video recording under Ubuntu.  My last project WebcamStudio was quite an adventure, but after 5 years as the project manager, I felt that it was time to move on to something else.  Don't worry, WebcamStudio is well and alive and currently maintained by Karl Ellis.  You can get the latest news by joining his G+ community "WebcamStudio Reloaded" ([https://plus.google.com/u/0/communities/110329269823088092206]("https://plus.google.com/u/0/communities/110329269823088092206")).

Since then, I worked on my youtube channel, creating some screencast from time to time.  The main issue when creating a screencast is finding a good software that is able to record in full HD, even if my laptop is not powerful enough for a full 30FPS.

So I ended up using ffmpeg/avconv from the console to record my desktop.  Once the recoding was done, I had to edit the video to add titles and my voice to comment what was happening on the screen.

Even if it worked quite well, I wanted to do it in one step and avoid doing some video editing.  Using that "complex" command in the terminal, I was able to achieve a screencast, with my webcam overlayed and also a banner:

```
avconv -r 10 -s 1366x768 -f x11grab -framerate 10 -video_size 1366x768 -i :0.0 -f video4linux2 -framerate 10 -video_size 320x240 -i /dev/video0 -f image2 -framerate 10 -i /tmp/screenstudio9094636433031284800.png -filter_complex [0:v]setpts=PTS-STARTPTS[desktop];[1:v]setpts=PTS-STARTPTS[webcam];[2:v]setpts=PTS-STARTPTS[banner];[desktop][webcam]overlay=main_w-overlay_w:main_h-overlay_h[newbackground];[newbackground][banner]overlay=0:main_h-overlay_h -f pulse -i  alsa_input.usb-Logitech_Logitech_USB_Microphone-00-Microphone.analog-mono -ar 44100 -vb 9000k -ab 128k -y /home/patrick/Broadcast/screenstudio.flv
```

It's cool, but I was stuck with 2 problems:  
[LIST]
[*]How to change the titles on my banner in an easy way
[*]How to avoid my terminal showing up at the start and the end of my video
[/LIST]

There are may ways to do this, but as I am a software developper, why not create something that would take care of this... :p

Drum roll....  ScreenStudio is born!

[IMG]http://screenstudio.crombz.com/screenstudio.png[/IMG]

ScreenStudio is a wrapper for avconv, thus making it easy to screencast your destop.  You can select your audio input, your webcam and your favorite banner to create your perfect screencast.

The project is open-source GPLV3 is available from the website of ScreenStudio: [http://screenstudio.crombz.com]("http://screenstudio.crombz.com")

Have fun!

---

### Post by kyle19 on 2014-04-29
Thanks so much, Ive been wanting to make tutorials for lubuntu on my youtube channel -3DActivated

---

### Post by nnjrob2 on 2014-04-29
This looks good, I'll give it a try

---

### Post by dannyboy79 on 2014-04-29
WOW, this is great. I am glad to see more and more options available for livestreaming. I currently use simplescreenrecorder and it works very very well always keeping the audio/video in sync which I always had issues with when using avconv or ffmpeg from the command line. The only thing missing is support for a webcam and compositing so that I could use an overlay. You refer to a "banner", is that an image that gets overlayed on top of your screenscast? 

Simplescreenrecorder was originally made for local recording to all sorts of formats but it does also work for livestreaming. I livestream on hitbox and will be doing so tonight at 8 pm CDT if you're interested in coming to check it out for a little bit. I livestream every Tuesday and Thursday at 8pm CDT until whenever and then on Sunday mornings at 9am until Noon. Since ssr doesn't have webcam support I have to open guvciview and set the window to "always on top" and I use devilspie to remove the window decoration so it appears like webcam support is built right into ssr.

If you program supports an overlay image than this is what I have been looking for. I use OBS when I play windows games and livestream in windows and until obs-studio is done with development i had to just stick with simplescreenrecorder and capture the screen vs capturing the game. I cant wait to try out your software.

---

### Post by patrickballeux on 2014-04-29
ScreenStudio is able to capture the desktop, even on slow PCs using a lower frame rate while keeping a great quality.  An overlay or banner can be applied using the provided banners or a custom PNG file by selecting Custom Banner.

Title and SubTitle will in overlay of everything so it's easy to set up your broadcast or screencast without having to learn the commands of avconv.

For now, ScreenStudio only supports one layout but as more options will be added in the future.

Thanks for your great comments.

For more examples and tutorials, have a look at my Youtube channel [http://youtube.com/patrickballeux]("http://youtube.com/patrickballeux")

---

### Post by dannyboy79 on 2014-04-30
I can't even get it to work. When I attempt to use it I get, "An error occured.." I looked for a .screenstudio folder within my home directory for a log but there's none. How would I troubleshoot why this isn't working?

---

### Post by FakeOutdoorsman on 2014-04-30
> **dannyboy79 said:**
> If you program supports an overlay image than this is what I have been looking for. I use OBS when I play windows games and livestream in windows and until obs-studio is done with development i had to just stick with simplescreenrecorder and capture the screen vs capturing the game. I cant wait to try out your software.

Some command line examples specific to streaming to the various live video sites: [Encoding for streaming site with FFmpeg](http://trac.ffmpeg.org/wiki/EncodingForStreamingSites). Includes examples of desktop recording with webcam and image/logo overlay. It's written for FFmpeg ([compile guide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)), so it may not work with forks.

---

### Post by dannyboy79 on 2014-04-30
> **FakeOutdoorsman said:**
> Some command line examples specific to streaming to the various live video sites: [Encoding for streaming site with FFmpeg](http://trac.ffmpeg.org/wiki/EncodingForStreamingSites). Includes examples of desktop recording with webcam and image/logo overlay. It's written for FFmpeg ([compile guide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)), so it may not work with forks.thanks for the link, i was familiar with that page. i always have issues with my video and audio becoming desync'd after a certain period of time so i've given up on ffmpeg command line streaming. I use simplescreenrecorder which has built in code to ensure sync between audio and video. I 'm just waiting for him to incorporate compositing OR for obs-studio to get finished

---

### Post by patrickballeux on 2014-04-30
Version 0.9 has a bug when streaming.  That is now fixed in 0.9.1 that is currently available.

As for the logs, you're right, I do expose the complete output on the console when running from the command line "java -jar ScreenStudio.jar".  The thing is that logging into a file could end-up in large files over time since the output is quite verbose.

Get the newest version.  I've made major modifications in this release.  See the latest Youtube video (ScreenStudio 0.9.1: New Look) for the details.

This new release also exposes the default configuration for AVCONV that you can now tweak to your liking.

---

### Post by patrickballeux on 2014-04-30
Here's the tutorial and demo for the version 0.9.1: [http://www.youtube.com/watch?v=xdFFLTVbb9A]("http://www.youtube.com/watch?v=xdFFLTVbb9A")

Still in beta mode, but getting better!

---

### Post by patrickballeux on 2014-04-30
Me too, the audio/video sync is a nightmare to solve.  Finally got it right in the ScreenStudio 0.9.1.

---

### Post by monkeybrain20122 on 2014-05-01
Cool stuffs! But I wonder why only flv is supported. flash is very problematic on Linux and many of us can't wait for its demise. :)

---

### Post by patrickballeux on 2014-05-01
FLV is mostly used for RTMP.  Flash does not matter as browsers are not able to play streams without the Flash plugin

---

### Post by dannyboy79 on 2014-05-02
i still get an error with version 0.9.2. here's the terminal output
```
ScreenStudio
-----------------------
Started
avconv -f video4linux2 -framerate 30 -itsoffset 0.0 -video_size 320x240 -i /dev/video0 -r 30 -f image2 -framerate 30 -i /tmp/screenstudio7903861705067230347.png  -f x11grab -video_size 1920x1080 -framerate 30 -i :0.1+0:0  -filter_complex [2:0][0:0]overlay=main_w-overlay_w:main_h-overlay_h[out];[out][1:0]overlay=0:main_h-overlay_h -f pulse -i  alsa_input.usb-046d_081a_13339CA0-02-U0x46d0x81a.analog-mono -r 30 -s 1280x720  -ar 44100 -vb 3000k -ab 128k -strict experimental -y -vcodec libx264  -preset veryfast -acodec libmp3lame -bufsize 4096k -f flv rtmp://live.hitbox.tv/push/ubuntuaddicted?key=XXXXXXXX/Stream Name
avconv version 0.8.10-6:0.8.10-0ubuntu0.13.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:53:28 with gcc 4.8.1
[video4linux2 @ 0xd95c40] Estimating duration from bitrate, this may be inaccurate
Input #0, video4linux2, from '/dev/video0':
  Duration: N/A, start: 2795.444967, bitrate: 36864 kb/s
    Stream #0.0: Video: rawvideo, yuyv422, 320x240, 36864 kb/s, 30 tbr, 1000k tbn, 30 tbc
Input #1, image2, from '/tmp/screenstudio7903861705067230347.png':
  Duration: 00:00:00.03, start: 0.000000, bitrate: N/A
    Stream #1.0: Video: png, bgra, 1920x150, 30 tbr, 30 tbn, 30 tbc
[x11grab @ 0xd532e0] device: :0.1+0:0 -> display: :0.1 x: 0 y: 0 width: 1920 height: 1080
[x11grab @ 0xd532e0] Could not open X display.
:0.1+0:0: Input/output error
Exit Code: 1
An error occured...

```
i made a comment on your youtube video but i'll post it here as well, i see in your avconv command you don't set the keyframe interval, both twitch and hitbox are very sensitive with this setting and if it's not set many times a black screen is what the websites player will show. just an fyi. If you're looking for any tips or help I would strongly suggest peaking at simplescreenrecorder source code

---

### Post by patrickballeux on 2014-05-08
I see the problem.  The issue is that ScreenStudio was trying to use the display 0.1 which does not exists actually.  This has been fixed in 0.9.3.

---

### Post by patrickballeux on 2014-05-08
I am working on the next release of ScreenStudio 1.0 and it will be great!

Basically, I am trying to build a pre-configured setup for any service so that anybody can easily broadcast their desktop.

Have a look at my youtube channel for the latest preview on ScreenStudio 1.0: [http://youtube.com/patrickballeux]("http://youtube.com/patrickballeux")

[IMG]http://1.bp.blogspot.com/-iywG9ezYQOE/U2w_EAuHzII/AAAAAAAAHIA/NdY2EmcyrXg/s1600/Screenshot+from+screenstudio-2014-05-08-21-41-01.flv.png[/IMG]

---

### Post by patrickballeux on 2014-06-21
ScreenStudio 1.2.0 is now available.  This is a major update over the previous versions.

Note:  The PPA is currently broken as some dependencies are missing.  It will be updated shortly.

Get it at [http://screenstudio.crombz.com]("http://screenstudio.crombz.com")

---

