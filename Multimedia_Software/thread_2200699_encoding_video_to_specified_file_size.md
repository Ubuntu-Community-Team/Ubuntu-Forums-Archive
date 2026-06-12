---
title: "encoding video to specified file size"
date: 2014-01-20
forum: Multimedia Software
---

### Post by kurja on 2014-01-20
It's been a while since I've worked with video, now I have a couple old tapes to digitize... It's going fine, but when exporting I can't find a way to export to a specified file size; I used to use a program (can't remember what it was)  where I could specify a maximum file size and the encoder adjusted accordingly, so I could be sure to get files that will fit on my target media. How could I achieve this, can anyone tell?

---

### Post by TheFu on 2014-01-20
What format do you need? That makes a huge difference in file size and the resulting playback quality.  A 700MB mpeg2 file will suck in quality compared to a 700MB xvid/avi or h.264/mp4 file.

mencoder
ffmpeg
avconv
avidemux

I think all those tools will do that.

---

### Post by SeijiSensei on 2014-01-21
I don't know if you can constrain the file sizes for all output formats, but you can do it with mencoder if you are encoding to AVI, usually with Xvid as the codec, and two-pass encoding. [Specifying a negative value for the bitrate]("http://en.linuxreviews.org/HOWTO_Convert_video_files#XviD_Encoding_using_mencoder") on the second pass tells mencoder to treat that value as the maximum file size.  It will then calculate the bitrate necessary to match that requirement.  Since you are encoding from tapes, Xvid in AVI will certainly provide sufficient video quality.

---

### Post by FakeOutdoorsman on 2014-01-21
See the two-pass encoding example at the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide#twopass).

---

### Post by uwe-bungto on 2014-01-21
How are you digitizing? I have used Kino over a firewire, it can export to a number of digital formats.

---

