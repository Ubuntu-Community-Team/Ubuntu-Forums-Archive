---
title: "AVI metadata?"
date: 2008-05-15
forum: Multimedia Software
---

### Post by danielsbrewer on 2008-05-15
I have a bunch of avi files that I will be creating and I would like to add metadata to them e.g. name, series, date etc. i.e. something like id3 tags for mp3s but for video files.  Does anyone know if this is possible?  Are there any other container formats that do support metadata.

If it is possible what programs are there to manipulate this metadata.  I plan to use mencoder to encode the files.

---

### Post by UberKnight on 2009-05-06
I'm also looking for a tool to automatically update video metadata (e.g. tv series info, etc.).

I came across [_Batch Metadata Tools_]("http://forums.freytechnologies.com/forums/showthread.php?t=34301"), a plugin for SageTV which is an htpc application, I think.

Is there any way to do this for video files on Ubuntu?

Regards
UberKnight

---

### Post by UberKnight on 2009-05-08
I found this thread ([http://ubuntuforums.org/showthread.php?t=921449&highlight=nfo](http://ubuntuforums.org/showthread.php?t=921449&highlight=nfo)) that seems to be discussing the same requirement and suggest an application called XBMC.

Will try it out, installation is a little complex, but managed to get it to show in synaptic thanks to a couple of other threads.

---

### Post by FakeOutdoorsman on 2009-05-08
FFmpeg can do this, but I haven't tried this.  Syntax for Jaunty Jackalope's FFmpeg:
```
ffmpeg -i input.avi -metadata title="Moonshine" -metadata author="Moonshine" -metadata copyright="2009" -metadata comment="foo" -acodec copy -vcodec copy output.avi
```
AtomicParsley is good for MP4:
```
AtomicParsley butterfly-ipod.mp4 --overWrite --artist "AlaskaRobotics.com" --title "Butterfly Kisses" --description "Watching butterflies flutter by" --copyright "©2009 Alaska Robotics"
```
So is MP4Box:
```
MP4Box -itags "name=mullet:artist=tennessee waterfall:comment=squirrel pelt" output.mp4
```

---

