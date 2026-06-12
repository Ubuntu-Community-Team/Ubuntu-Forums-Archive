---
title: "VOB to single MPEG file (uncompressed) - how?"
date: 2013-02-19
forum: Multimedia Software
---

### Post by MrsUser on 2013-02-19
Hello to all you video buffs :)

I have a video dvd which I copied to my hard disk, i.e. I have the VIDEO_TS folder with the VOB files in it. I want to convert those VOB file segments of the main movie into one big, uncompressed *.MPEG file. I can open and append them in Avidemux, where I chose MPEG as the container format and 'copy' for both audio and video. The video length is displayed correctly and I can play it in Avidemux. However, when I save the MPEG to hdd, the file is missing the audio and is too short, which means it doesn't save the whole movie, about 25% at the end is missing -- and no, I haven't set any edit markers. Are there any alternatives to do this? Any help is appreciated.

---

### Post by andrew.46 on 2013-02-19
Try copying to your HDD with dvdbackup, try *dvdbackup --mirror* and see if that catches all of the dvd...

---

### Post by MrsUser on 2013-02-19
> **andrew.46 said:**
> Try copying to your HDD with dvdbackup, try *dvdbackup --mirror* and see if that catches all of the dvd...
Have you read my post? ^^
I have already copied the DVD to hard disk. And dvdbackup will do just this. But what I need is to convert the *.VOB blocks of the main movie into one single MPEG file.

---

### Post by evilsoup on 2013-02-19
If you know which VOB files you want to copy together - which ones represent the actual film, this is normally the set of VOBs with the most parts - you can just use ffmpeg's concat protocol.

```

ffmpeg -i 'concat:VTS_01_1.VOB|VTS_01_2.VOB|VTS_02_3.VOB' -map 0 -c copy combined.mpeg

```

You may need to use '-acodec copy -vcodec copy' instead of '-c copy', you may need to drop the '-map 0'. You can have as many vob files in the concat protocol as you want. To avoid hassle, use the version from [this PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg).

---

### Post by MrsUser on 2013-02-19
> **evilsoup said:**
> If you know which VOB files you want to copy together - which ones represent the actual film, this is normally the set of VOBs with the most parts - you can just use ffmpeg's concat protocol.

```

ffmpeg -i 'concat:VTS_01_1.VOB|VTS_01_2.VOB|VTS_02_3.VOB' -map 0 -c copy combined.mpeg

```You may need to use '-acodec copy -vcodec copy' instead of '-c copy', you may need to drop the '-map 0'. You can have as many vob files in the concat protocol as you want. To avoid hassle, use the version from [this PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg").

I had no ffmpeg installed, simply tried it with avconv and it works (but without the '-map' parameter only) And the mpeg is obviously correct and plays fine. However, for some reason the audio is out of sync, comes about 2 seconds too early :-/

---

### Post by andrew.46 on 2013-02-19
> **MrsUser said:**
> Have you read my post? ^^

Indeed I have, one possibility is that you have incompletely copied your movie to your HDD...

---

### Post by MrsUser on 2013-02-19
> **andrew.46 said:**
> Indeed I have, one possibility is that you have incompletely copied your movie to your HDD...

No, it's complete. I can play the copied structure from beginning to end in VLC, nothing missing. Anyway, evilsoup's method works, except for having the audio too early. I'm trying to figure out how to fix that, maybe somehow a delay can be defined, I don't know.

EDIT:
Here's how I did it (copying only the second audio track):

```
avconv -i 'concat:VTS_02_1.VOB|VTS_02_2.VOB|VTS_02_3.VOB|VTS_02_4.VOB|VTS_02_5.VOB' -map 0:v -map 0:a:2 -acodec copy -vcodec copy combined-only-second-audio-track.mpeg
```

-map 0:v -- copies all video tracks
-map 0:a:2 -- copies only the second audio track

However, the audio track must be in a compatible format for the container. AC3 is fine. Then I put everything in an MKV with mkvmergeGUI (mkvtoolnix), adding 1000 (ms) in the format specific options of the audio track. Now it's all in one container and in sync :)

---

### Post by andrew.46 on 2013-02-19
There is the *-itsoffset* option but this can be a bit painful to use...

---

### Post by MrsUser on 2013-02-20
> **andrew.46 said:**
> There is the *-itsoffset* option but this can be a bit painful to use...

Thank you for that hint! It was actually easy to use:

```
avconv -itsoffset -1 -i 'concat:VTS_02_1.VOB|VTS_02_2.VOB|VTS_02_3.VOB|VTS_02_4.VOB|VTS_02_5.VOB' -map 0:v -map 0:a:1 -acodec ac3_fixed -b:a 192k -vcodec copy combined.mpeg
```I've set -itsoffset to '-1' which means the video stream(s) of the input file start(s) 1 second earlier. It doesn't affect the audio streams. And it worked fine, now the video comes 1 second earlier as the audio did and both are in sync now. I also encoded the second audio track to ac3 with 192kbps  on the fly. Actually, command line encoding is pretty much awesome and powerful, and in particular also much faster than with GUI. However, it can be a pain to figure out everything manually.

---

### Post by andrew.46 on 2013-02-20
Great to hear that it has all worked out for you :). If you are really keen on FFmpeg perhaps look up FakeOutdoorsman's wiki page some time soon, grab a recent version of FFmpeg and delve a little deeper into a truly amazing commandline application...

---

### Post by sudodus on 2013-02-20
Thank you all for valuable tips :KS

I'm reading and learning :-)

---

### Post by evilsoup on 2013-02-20
+1 to andrew.46's recommendation to upgrade to a more recent version; ffmpeg & avconv both have very rapid development times, so bugs (maybe even including this problem with A/V sync in those VOBs) are frequently fixed in newer versions that those in the repos.

---

### Post by MrsUser on 2013-02-20
> **andrew.46 said:**
> Great to hear that it has all worked out for you :). If you are really keen on FFmpeg perhaps look up FakeOutdoorsman's wiki page some time soon, grab a recent version of FFmpeg and delve a little deeper into a truly amazing commandline application...
Do you have a link?

---

### Post by FakeOutdoorsman on 2013-02-20
> **MrsUser said:**
> Do you have a link?

The [FFmpeg Community Contributed Documentation Wiki](http://ffmpeg.org/trac/ffmpeg/wiki#CommunityContributedDocumentation) contains all sorts of guides and examples to supplement the official [FFmpeg documentation](https://ffmpeg.org/documentation.html) in a more user-friendly and step-by-step format.

---

### Post by MrsUser on 2013-02-20
> **FakeOutdoorsman said:**
> The [FFmpeg Community Contributed Documentation Wiki]("http://ffmpeg.org/trac/ffmpeg/wiki#CommunityContributedDocumentation") contains all sorts of guides and examples to supplement the official [FFmpeg documentation]("https://ffmpeg.org/documentation.html") in a more user-friendly and step-by-step format.
Thanks! It's a great guide. Just what I need. I really like how efficient the results are with the command line. I wouldn't use it for stuff like cropping though, but for basic transcoding it's very straightforward and fast.

---

### Post by FakeOutdoorsman on 2013-02-20
> **MrsUser said:**
> I really like how efficient the results are with the command line. I wouldn't use it for stuff like cropping though

Cropping via command line is easy once you try it a few times, and you can use ffplay to get a quick preview. Imagine this input is 640x480 and I want to remove 40 pixels: 20 from the top and 20 from the bottom to make an output of 640x440:

```
ffplay -i input -vf crop=iw:ih-40
```

Is same as:
```
ffplay -i input -vf crop=640:480-40
```

Is same as:
```
ffplay -i input -vf crop=640:440
```

Then you can use ffmpeg to crop and re-encode the video and copy the audio stream since you don't need to process it which can preserve quality and is faster than encoding:

```
ffmpeg -i input -vf crop=iw:ih-40 -codec:v libx264 -crf 23 -preset medium -codec:a copy output.mkv
```

See the [filtering introduction](https://ffmpeg.org/ffmpeg-filters.html#Filtering-Introduction) and [crop documentation](https://ffmpeg.org/ffmpeg-filters.html#crop) for more examples.

---

