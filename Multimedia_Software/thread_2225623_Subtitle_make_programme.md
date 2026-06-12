---
title: "Subtitle make programme"
date: 2014-05-22
forum: Multimedia Software
---

### Post by Tarek_Aboabdallah on 2014-05-22
Hello every one,
I'm new at Ubuntu and I want a programme that allow me to create srt files and make subtitle to videos 
On windows I used "Cyberlink Power Director"
so any one can give me a programme that I can use on Ubuntu "it must be free"[RIGHT][COLOR=#545454][FONT=arial][/FONT][/COLOR][/RIGHT]
And thanks a lot

---

### Post by Tarek_Aboabdallah on 2014-05-22
Hello every one,
I'm new at Ubuntu and I want a programme that allow me to create srt files and make subtitle to videos 
On windows I used "Cyberlink Power Director"
so any one can give me a programme that I can use on Ubuntu "it must be free"[RIGHT][COLOR=#545454][FONT=arial][/FONT][/COLOR][/RIGHT]
And thanks a lot

---

### Post by slickymaster on 2014-05-22
Moving this thread into the **General Help** sub-forum since it's a support question.

---

### Post by Impavidus on 2014-05-22
In the repositories for 14.04 I see gnome-subtitles, subtitleeditor, subtitlecomposer (for KDE) and others. Open the software centre, search for "subtitle" and try one (or all).

---

### Post by SeijiSensei on 2014-05-22
Anime fansubbers largely rely on [Aegisub]("http://www.aegisub.org/"). You can install it from the Ubuntu repositories using "sudo apt-get install aegisub".  There are also versions for Windows and OS X.

---

### Post by Tarek_Aboabdallah on 2014-05-22
> **SeijiSensei said:**
> Anime fansubbers largely rely on [Aegisub]("http://www.aegisub.org/"). You can install it from the Ubuntu repositories using "sudo apt-get install aegisub".  There are also versions for Windows and OS X.


Well I tried it, but that's didn't what I need
I want a programme that allow me to put the subtitle into a video and then rendering it to make the subtitle from the video not a srt file :(

---

### Post by Tarek_Aboabdallah on 2014-05-22
Thanks I will try them :)

---

### Post by coffeecat on 2014-05-22
Threads merged. Please do not post duplicates. This dilutes community effort.

---

### Post by Tarek_Aboabdallah on 2014-05-22
Well non of them what I'm looking for :(
I want a programme that allow me to make subtitle for the video and then rendering them together so the subtitle will be part of the video 
Not srt file :(

---

### Post by SeijiSensei on 2014-05-23
You mean you want to take a video and an srt file and "burn" the subtitles into the video?  That's pretty easy to do from the command prompt:  [http://linuxg.net/how-to-embed-subtitles-to-movies-with-mencoder-and-ffmpeg/](http://linuxg.net/how-to-embed-subtitles-to-movies-with-mencoder-and-ffmpeg/)

---

### Post by ortermagic on 2014-05-23
I suppose you could try Kdenlive, I find it quite useful it's in software center

---

### Post by FakeOutdoorsman on 2014-05-25
Sounds like you want "hardsubs", or to "burn-in" the subtitles.

1. [Download ffmpeg](https://ffmpeg.org/download.html#LinuxBuilds) (the repository version does not have subtitles filter, IIRC, and 14.04 does not provide ffmpeg)
2. Then see [How to burn subtitles/add hardsubs with ffmpeg](http://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo).

Example:
```
ffmpeg -i video.mkv -vf subtitles=subs.srt -acodec copy output.mkv
```

Notes:
[list]
[*]Adding hardsubs will require re-encoding. See the [FFmpeg and x264 Encoding Guide](http://trac.ffmpeg.org/wiki/x264EncodingGuide) for more info on that.
[*]This example simply [stream copies](https://ffmpeg.org/ffmpeg.html#Stream-copy) (re-muxes) the audio, so it is not re-encoded.
[*]You can use Aegisub as mentioned by SeijiSensei to create your SRT file, or you can possibly download one.
[/list]

---

