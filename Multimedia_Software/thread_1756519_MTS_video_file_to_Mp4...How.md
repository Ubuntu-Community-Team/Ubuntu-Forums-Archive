---
title: "MTS video file to Mp4...How ?"
date: 2011-05-12
forum: Multimedia Software
---

### Post by zhivago1955 on 2011-05-12
How do you convert AVCHD video file (MTS) to MP4 or WMV? Which program on Ubuntu do I use? 

THX

Zhivago1955,

Oregon, USA

---

### Post by handy on 2011-05-12
You could try HandBrake.

It is not in the standard Ubuntu repo due to some library licensing legality or some such rubbish.

So you'll have to do a quick search for the how-to install, which will be a simple process.

[edit:] I did a quick search myself:

[http://www.jonathanmoeller.com/screed/?p=2991](http://www.jonathanmoeller.com/screed/?p=2991)  

/edit

It is brilliant software, so if for some strange reason it doesn't handle your problem here, I'm sure you will be happy to use it under other more straight forward sets of circumstances.

---

### Post by sudodus on 2012-07-20
If ***HandBrake*** works for you, fine :-)

Otherwise you can try ***OpenShot*** (it is in the repos)
or if you can manage terminal window commands ***ffmpeg***.

See for example this link [[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1920371_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1920371")

---

### Post by FakeOutdoorsman on 2012-07-22
FFmpeg can do this, and since MTS usually contains H.264 video (which MP4 supports) then you can simply copy the video from MTS to MP4.
```
ffmpeg -i input.mts -vcodec copy -acodec libfaac -aq 100 -ac 2 output.mp4
```
You can get *libfaac*, an AAC encoder, with the **libavcodec-extra-53** package (or 52 if you're using older Ubuntu) from Medibuntu. See instructions here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Otherwise use *-acodec aac -strict experimental -ab 192k* (and remove *-aq 100*) or if you're using recent Ubuntu use *-acodec libvo_aacenc -ab 192k* (and remove *-aq 100*).

You can probably copy the audio instead of re-encoding since MP4 supports AC-3, but I don't know if your input contains this and since you didn't provide many details I'm guessing you want the more familiar combination of H.264/AAC.

---

### Post by gordintoronto on 2012-07-22
Even better, install winff and do the setup in a GUI.

---

