---
title: "Commands required to convert videos to webm format."
date: 2015-07-05
forum: Multimedia Software
---

### Post by Rytron on 2015-07-05
Hi guys.

I'd like a command to convert individual videos (mostly flv, mp4) to webm.

Also I'd like a command to batch convert videos (again mostly flv, mp4) to webm.

I'd like to keep the audio and video bitrate the same or maybe slightly lower than the original video. Perhaps 128kbps would suffice for the audio?

Thanks all.

---

### Post by Rytron on 2015-07-05
Out of curiosity -- what would happen if the output bitrate for video and or audio was higher than the original? Would this just be wasted extra file space?

---

### Post by mc4man on 2015-07-05
You would need to experiment as to what bitrate or quality suits your purposes. Note that vp9 encoding is slow so fool around with some small representative  files to start.
Read 
[http://wiki.webmproject.org/ffmpeg/vp9-encoding-guide](http://wiki.webmproject.org/ffmpeg/vp9-encoding-guide)
maybe here - 
[http://wiki.webmproject.org/adaptive-streaming/instructions-to-playback-adaptive-webm-using-dash](http://wiki.webmproject.org/adaptive-streaming/instructions-to-playback-adaptive-webm-using-dash)

Or you could try dmMediaConverter, $3 in software-center, free from here. It uses pop up tips to guide you, have only tested a couple of times in the past so have no experience with
[https://drive.google.com/folderview?id=0B1MiTYJef5a9TG9kMC04WWE3YkU&usp=sharing#list](https://drive.google.com/folderview?id=0B1MiTYJef5a9TG9kMC04WWE3YkU&usp=sharing#list)

(whether it violates any ffmpeg licensing no clue...

---

### Post by helicase on 2015-07-05
A straight conversion to webm should be very easy:

```
avconv -i <input file> <output file>.webm
```

avconv does all the thinking for you in this case, but you can change anything you like, really: -b changes the video bitrate and -ab the audio bitrate, for example. So changing the audio to 128kbps would give you:
```

avconv -i <input file> -ab 128k <output file>.webm
```

---

### Post by Rob Sayer on 2015-07-06
The only way I know of to get a smaller file size with comparable quality would be to use a higher profile and/or downsample the video resolution.

---

### Post by Rytron on 2015-07-06
How can I bulk convert to webm and match the original audio and video bitrates?

---

### Post by Rytron on 2015-07-07
> **helicase said:**
> A straight conversion to webm should be very easy:

```
avconv -i <input file> <output file>.webm
```

avconv does all the thinking for you in this case, but you can change anything you like, really: -b changes the video bitrate and -ab the audio bitrate, for example. So changing the audio to 128kbps would give you:
```

avconv -i <input file> -ab 128k <output file>.webm
```

Unfortunately the video quality is very poor at default settings.

---

### Post by mc4man on 2015-07-07
> **Rytron said:**
> Unfortunately the video quality is very poor at default settings.
Well then raise the br to suit your perception & the combo of source material & target device/use
What may look ok on a phone could be awful on a laptop/monitor ect.

For vp8 try at least 1000  kb/s, probably more.
(vp9 is a superior encoder but *much* slower than vp8, could be 6x or so the vid length time wise to encode, depends on hardware, 1 or 2 pass, ect.

---

### Post by mc4man on 2015-07-07
Just to note as using ffmpeg sort of is at odds with whatever you're up to.
in some timed tests I've found libvpx-1.4 to be significantly faster than version 1.3.
(- still slow depending on the source & output. 1080 is slower than 720 than 480, ect. So a 1080p to 1080p took 25 min. for 2 pass on a 4.5 min. vid. 720p would be about 40% less time. With 1.3 while I didn't actually time it was at least 45 min. for the 1080 vid if not a bit longer.

---

