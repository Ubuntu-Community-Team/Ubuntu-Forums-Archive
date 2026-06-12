---
title: "Choppy video playback with ac3 in VLC"
date: 2008-08-23
forum: Multimedia Software
---

### Post by miceagol on 2008-08-23
I have problems with slightly choppy video playback with video files that have ac3 audio (including DVD's), that is, there's a slight pause in playback every 20 seconds or so. I have tested video files with e.g. mp3 audio, and there is no such problems with those files.

My audio setup is as follows:
Sound card => M-audio Revolution 5.1
Output => Digital Coaxial S/PDIF connected to [this amplifier]("http://www.xtz.se/produkt.php?allmant=true&produkt=5&eng=true")

[This is my VLC configuration file]("http://folk.uio.no/michaeka/tilverden/vlcrc"), and my .asoundrc file looks like this:
```

pcm.!default {
	type plug
	slave.pcm "iec958:CARD=Revolution51,DEV=0" # taken from aplay -L
}

```

Does anyone have any inputs on how it may be fixed? In mplayer I cannot play files with ac3 audio at all, but I have described that problem in [a separate thread]("http://ubuntuforums.org/showthread.php?p=5648489").

---

