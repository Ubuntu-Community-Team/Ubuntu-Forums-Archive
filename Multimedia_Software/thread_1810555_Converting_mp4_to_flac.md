---
title: "Converting mp4 to flac"
date: 2011-07-23
forum: Multimedia Software
---

### Post by Spae on 2011-07-23
I converted using a simple app called sound converter to convert my mp4 vids to flac (because they were music i didn't need the picture.)

The only problem I have is the file sizes have jumped a lot! 

Which is bad because one of the main reasons I wanted to convert is because i thought removing video reduced the file size.

For example one file went from 6.4mb mp4 to a 19.7mb flac.
And the rest are similair stories.

---

### Post by ron999 on 2011-07-23
....

---

### Post by shantiq on 2011-07-23
hi spae what this means is that your video files must be really low quality picture if they are so small or very short

Flac is lossless and will bump up your kbps to say at least 400 therefore ending up with a file that is bigger than the original video+audio file

so i would suggest finding out what the audio quality is on any of the mp4 files


to do this check properties or else do  (you need ffmpeg)

```
ffmpeg -i  nameofyourfile.mp4
```

===============================
[B]More involved route
[/B]

say you find your kbps is 160 or 96 or 128  which i guess it probably is or thereabouts then i would suggest if the audio
in a smaller size is what you want to run

cd   change directory to where your video files are then ( for one file or many at once)

```
for f in *.mp4; do ffmpeg -i "$f" -ab **[COLOR="Red"]128k [/COLOR]**"${f%.mp4}.mp3"; done

```


change the 128 to match original kbps


which will give you an **mp3** of exactly the same audio size as your original audio in the video file


i hope this is what you need and that my explanations are clear and make sense to you


ask if you need clarifications   shan


============================================================================
[B][FONT="Comic Sans MS"]
[SIZE="2"]or if you want it [SIZE="3"]simple[/SIZE][/SIZE]

use sound converter  again or soundkonverter but this time pick mp3 **or** m4a instead of flac and pick the matching kbps   probably the normal setting see attached image[/FONT][/B]

---

### Post by coffeecat on 2011-07-23
If you want to strip out the audio without converting it, try using Avidemux. Make sure Audio is set to "copy" in the main window, and then from the Audio menu, choose save. You need to specify the audio filename extension, so to see what audio codec it is, right-click on the original video file -> Properties -> Video/Audio tab.

---

