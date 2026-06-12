---
title: "Bizarre behaviour with avconv using webcam and GIF format"
date: 2013-02-10
forum: Multimedia Software
---

### Post by Paddy Landau on 2013-02-10
I have a command to take a photo with the webcam using [FONT=Lucida Console]ffmpeg[/FONT]:
```
[COLOR=Gray]$[/COLOR] ffmpeg -f video4linux2 -i /dev/video0 -vframes 1 photo.jpg
```As [FONT=Lucida Console]ffmpeg[/FONT] has been deprecated for some time, I thought I would experiment with [FONT=Lucida Console]avconv[/FONT].

Experimenting, I find that [FONT=Lucida Console]avconv[/FONT] is sensitive to the extension of the file. Omitting the extension always gives an error. However, I have found bizarre behaviour with gif. Look at the following.

Take a gif photo:
```
[COLOR=Gray]$[/COLOR] avconv -loglevel warning -f video4linux2 -i /dev/video0 -frames 1 -codec gif -pix_fmt rgb8 photo.gif
[COLOR=DarkOrange][video4linux2 @ 0x1388a60] Estimating duration from bitrate, this may be inaccurate[/COLOR]
[COLOR=Red][gif @ 0x13892c0] ERROR: gif only handles the rgb24 pixel format. Use -pix_fmt rgb24.
Could not write header for output file #0 (incorrect codec parameters ?)[/COLOR]
```That creates an empty [FONT=Lucida Console]photo.gif[/FONT] file.

But if I change the file extension to [FONT=Lucida Console].jpg[/FONT], [FONT=Lucida Console]avconv[/FONT] works:
```
[COLOR=Gray]$[/COLOR] avconv -loglevel warning -f video4linux2 -i /dev/video0 -frames 1 -codec gif -pix_fmt rgb8 photo.jpg
[COLOR=DarkOrange][video4linux2 @ 0x977a60] Estimating duration from bitrate, this may be inaccurate[/COLOR]
[COLOR=Gray]$[/COLOR] file photo.jpg
photo.jpg: GIF image data, version 89a, 640 x 480
[COLOR=Gray]$[/COLOR] mv photo.jpg photo.gif
[COLOR=Gray]$[/COLOR] xdg-open photo.gif    # This works
```[FONT=Lucida Console]avconv[/FONT], fortunately, does not have this problem when using other formats such as png, bmp and jpg (although targa must have extension [FONT=Lucida Console].tga[/FONT]).

Is this a bug that needs raising? Or have I missed something in the command line?

---

### Post by FakeOutdoorsman on 2013-02-11
> **Paddy Landau said:**
> As [FONT=Lucida Console]ffmpeg[/FONT] has been deprecated for some time...

You can say this for the bizarro, fake "ffmpeg" in the repository, where its upstream was libav, but not for real ffmpeg from FFmpeg where development is very active.

I just replied in [another thread](http://ubuntuforums.org/showpost.php?p=12503609&postcount=11) with more details.

---

### Post by Paddy Landau on 2013-02-11
Thank you, FakeOutdoorsman. I shall reply to your other post shortly.

---

### Post by FakeOutdoorsman on 2013-02-11
Sorry for the distraction of the eariler post, but you simply need to add "-pix_fmt rgb24" as an output option when you want to output to gif; at least with real ffmpeg and apparently avconv too. I don't know why this isn't default behavior.

---

### Post by Paddy Landau on 2013-02-11
> **FakeOutdoorsman said:**
> … you simply need to add "-pix_fmt rgb24" as an output option when you want to output to gif
Thank you. I could have sworn that I had tried that!

Now, avconv creates the GIF, but terribly distorted. Never mind; I shall use ffmpeg thanks to [post=12503609]your enlightening post[/post] (I have [post=12503724]replied to it[/post] with a couple of questions).

---

### Post by FakeOutdoorsman on 2013-02-11
I can confirm the crappy output using current ffmpeg from FFmpeg, but if I convert the jpg output to gif using the Gimp or "convert" from imagemagick then it is much better looking, so there is room for improvement AFAIK.

So for now if you must have a gif then I recommend outputting to a high-quality image from ffmpeg and then using "convert" on it to make the gif.

Or just use png and ignore gif.

---

### Post by Paddy Landau on 2013-02-12
Thank you. I shall follow your advice. I think it's time to mark this thread as solved.

---

### Post by FakeOutdoorsman on 2013-02-12
This gif stuff is confusing me. Apparently there are two gif encoders in ffmpeg...I guess.

```
ffmpeg -i input -f image2 output.gif
```

It makes a slightly better looking output. I'll solve this issue for myself by continuing to ignore gif!

---

### Post by Paddy Landau on 2013-02-12
> **FakeOutdoorsman said:**
> I'll solve this issue for myself by continuing to ignore gif!
LOL, good advice!

---

