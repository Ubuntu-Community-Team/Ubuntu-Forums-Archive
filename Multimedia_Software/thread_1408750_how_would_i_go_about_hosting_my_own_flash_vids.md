---
title: "how would i go about hosting my own flash vids"
date: 2010-02-16
forum: Multimedia Software
---

### Post by nerdy_kid on 2010-02-16
So i have this blog, and i want to embed flash vids in it like YouTube.  However, i want to do this from my apache2 web server, partly for bragging rights among my non-techie circle of friends, but mostly because I cant get YouTube to do what i want (which is private viewing of vids by non-youtube members)

any tips on how to do this?

---

### Post by Warpnow on 2010-02-17
[http://www.w3schools.com/flash/flash_inhtml.asp](http://www.w3schools.com/flash/flash_inhtml.asp)
```

<object width="550" height="400">
<param name="movie" value="somefilename.swf">
<embed src="somefilename.swf" width="550" height="400">
</embed>
</object>

```

Use ffmpeg to turn the vids into swf files.

---

### Post by FakeOutdoorsman on 2010-02-17
> **nerdy_kid said:**
> any tips on how to do this?

I'm doing this with FFmpeg and a custom Flash player, but the last few days I've been working on migrating to JW Player because it is free for non-commercial use and not too expensive for a commercial license.  Another free player is Flowplayer.

I encode video using a self-compiled FFmpeg.  I compile it myself because development is very active and it's nice to take advantage of all of the bug fixes and additions that the repository version lacks.  I wrote a guide showing how to do this:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Now for an encoding example using FFmpeg:
```
ffmpeg -i input.avi -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -wpredp 0 -crf 26 -threads 0 ffmpegoutput.mp4
```

See the [FFmpeg x264 Encoding Guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for a good encoding primer.  I added *-wpredp 0* because of a bug in Adobe Flash Player (fixed in upcoming version 10.1).  You may want to experiment on the above example.

Now run the FFmpeg output through qt-faststart or MP4Box (part of the **gpac** package).  This allows your video to play before it's completely downloaded.  qt-faststart is included in the source code of FFmpeg.  If you followed the FFmpeg compilation guide:
```
cd ~/ffmpeg/tools
make qt-faststart
sudo cp qt-faststart /usr/local/bin
```

Now to use qt-faststart (note that the input and output can't be the same file):
```
qt-faststart ffmpegoutput.mp4 finaloutput.mp4
```
or use MP4Box:
```
MP4Box -add ffmpegoutput.mp4 finaloutput.mp4
```

Now use one of the Flash players that I mentioned to play your video.  I currently encode two videos for each title and allow the user to have a choice between HD and SD via a free plugin.

---

### Post by frup on 2010-02-17
Come on! Use HTML5! :P

---

### Post by nerdy_kid on 2010-02-17
ahhh thanks for the very usefull responses!  I am going to go the ffmpeg to swf route thanks a ton guys! :D

---

### Post by FakeOutdoorsman on 2010-02-17
> **nerdy_kid said:**
> ahhh thanks for the very usefull responses!  I am going to go the ffmpeg to swf route thanks a ton guys! :D

Using FFmpeg to encode a video with the swf extension automatically chooses *-vcodec flv*, which is a poor quality and stagnant encoder compared to *libx264* as described in my post above.

---

### Post by nerdy_kid on 2010-02-17
> **FakeOutdoorsman said:**
> Using FFmpeg to encode a video with the swf extension automatically chooses *-vcodec flv*, which is a poor quality and stagnant encoder compared to *libx264* as described in my post above.

ok, once i get everything set up and working properly then start messing with the video formats some more.  Thanks very much, you all have been very helpful! :)

---

