---
title: "convert tivo to mpeg 2 for burning onto DVD"
date: 2013-01-25
forum: Multimedia Software
---

### Post by Merrattic on 2013-01-25
How are you converting?

---

### Post by evilsoup on 2013-01-25
Are you open to using the command-line? I would use ffmpeg:

```

ffmpeg -i input.mp4 -target pal-dvd output.mpg

```Use 'ntsc-dvd' [if you're in]("http://en.wikipedia.org/wiki/File:PAL-NTSC-SECAM.svg") an NTSC area. The -target option will:


[LIST]
[*]Scale the image down to the correct height (576 for PAL, 480 for NTSC)
[*]Use the correct frame-rate (25 for PAL, 29.97 for NTSC)
[*]Convert the video to mpeg2 with good quality settings
[*]Convert the audio to AC3 with good quality settings
[/LIST]
If you want to set things manually, you can select a quality level using -qscale:v or -q:v - unfortunately, AC3 audio only has a constant bit rate mode, but 192kb/s should be adequate for stereo audio:


```
 
ffmpeg -i input.file -filter:v 'scale=-1:576' -c:v mpeg2video -q:v 3 -c:a ac3 -b:a 192k output.mpg

```For -q:v you can use any value from 1-31, where 1 is best quality and 3-6 can generally be considered a useful range. Use the highest number that looks OK to you.


-filter:v 'scale=-1:576' tells ffmpeg to scale the video down to a height of 576 pixels, while scaling the width to keep the same aspect ratio. It may not work in the version of ffmpeg in the repositories, but you can upgrade to a more recent version using [this PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg").

---

