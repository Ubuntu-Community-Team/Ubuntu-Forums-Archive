---
title: "Merging video with a data file"
date: 2016-06-12
forum: Multimedia Software
---

### Post by aeronutt on 2016-06-12
I'm not a programmer, but can write simple scripts (various languages), and very basic C.

How difficult would it be to merge a video file (with gps time stamps) with a .cvs file (or other format) that has 2 or 3 data types along with gps time stamps.
The end result being a video, with the data showing on the video in a simple text format, time synchronized.

Use example; video of vehicle moving on road, plus a data file (obviously from a different device than the video camera) that has captured a few things like speed and gps location, for example. (Video and data captured within same time frame.)

Any currently supported linux video editing tools that have an API I could understand that I could interface the data files to, or some sort of input format for text based files to merge with the video?

---

### Post by yoshii on 2016-06-13
You could investigate MKVtoolNix, the Matroska tools.  
You might be able to put the GPS data into a subtitle/caption file and then merge that into the MKV container along with the video and any other related data.  
The Matroska format is nice because if you make mistakes, you can take it apart, fix it, and put it back together again.  And it can store the original files if they are compatible.  

I don't know anything about editing subtitle files, however.

---

### Post by SeijiSensei on 2016-06-13
The most widely-used tool for editing subtitles is [Aegisub]("http://www.aegisub.org/"), long a mainstay among anime fansubbers.  The [Advanced Substation Alpha]("https://en.wikipedia.org/wiki/SubStation_Alpha#Advanced_SubStation_Alpha") ("ASS") format provides a wide range of control over colors, fonts, screen location, and the like.  There are .deb packages of Aegisub for Linux [here]("http://ftp.aegisub.org/pub/releases/"), but it's primarily designed for Windows.  The most recent version doesn't have a Linux version, and I encountered problems compiling my own copy out of curiosity even after installing the various dependencies it required.

---

### Post by FakeOutdoorsman on 2016-06-13
I second SeijiSensei's recommendation to use ASS. It gives you the choice of softsubs or hardsubs. Using softsubs will allow you to keep the video as-is with no re-encoding.

softsubs:
```
ffmpeg -i video -i subtitles.ass -map 0 -map 1 -c copy output.mkv
```

hardsubs:
```
ffmpeg -i video -filter_complex subtitles=subtitles.ass -c:a copy output
```

Alternatively, you could use SRT subtitle format. It is simpler than ASS.

---

### Post by X-RED_Tech on 2016-06-13
> **SeijiSensei said:**
> The most widely-used tool for editing subtitles is [Aegisub]("http://www.aegisub.org/"), long a mainstay among anime fansubbers.  The [Advanced Substation Alpha]("https://en.wikipedia.org/wiki/SubStation_Alpha#Advanced_SubStation_Alpha") ("ASS") format provides a wide range of control over colors, fonts, screen location, and the like.  There are .deb packages of Aegisub for Linux [here]("http://ftp.aegisub.org/pub/releases/"), but it's primarily designed for Windows.  The most recent version doesn't have a Linux version, and I encountered problems compiling my own copy out of curiosity even after installing the various dependencies it required.

Aegisub 3.2.2 is available for 16.04 at the official repositories.

---

### Post by aeronutt on 2016-06-14
Thanks for the guidance, I'll check these out!!

---

### Post by aeronutt on 2016-06-14
Installed aegisub, and at first look this could work really well, and easy. The format of the text files that you can use to import subtitles is simple and I can (hopefully) easily write a script to convert from my non-video (gds, speed, location, etc) devices format.  Yaaa!

Now, I just have to figure out how to view gps time meta-data in a video, and align start times of a video and my data files.
What's a good tool to view meta-data in a video file?
(Ya know, I'm assuming GPS time stamps are saved *in* the video file from devices like go-pro and garmin video cams. Hmmm. I'd better look into that.)

EDIT: ok, at least some of the meta data can be extracted using exifdata or mediainfo. Now, trying to get a sample of native video from a garmin VIRB.

---

### Post by FakeOutdoorsman on 2016-06-15
Can you provide a short sample video that contains the data?

---

### Post by aeronutt on 2016-06-15
> **FakeOutdoorsman said:**
> Can you provide a short sample video that contains the data?

I will as soon as I get one off the platform I'm considering, the garmin VERB XE. Should have something native off of a VERB by this weekend. It'd be great for someone else that knows what they're doing to take a quick look at it!

Because of the great help from you folks so far, let me add a little more info into what/why I'm doing this:

This will be used mostly to look at motorsports results (just mine). There are many commercial solutions out there that do this very well, but none that I can find that run on Linux. Plenty that run on Android, Iphone, or Windows. I've tried 'wine', with little luck, and I only have XP on my virtual machine. My short term plan is to use an Android device with a commonly used app to collect data about the event (timing, accelerometer data, speed, plus possibly location). And use a Garmin VERB (or a GoPro) to collect video.  Then, use my Linux PC to overlay the data onto the video (in very simple text format; the commercial solutions are much fancier, replicating rpm and speedometer gauges, etc).  Make sense?

Here's an example of what one can find from the raw data from the Android app that collects info (without vid).

[img]http://i.imgur.com/gUzETt3.png?1[/img]

---

