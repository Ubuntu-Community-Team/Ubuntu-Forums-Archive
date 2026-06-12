---
title: "Convert png to video"
date: 2013-09-07
forum: Multimedia Software
---

### Post by scamiolo on 2013-09-07
Hi guys

I hope not to replicate existing threads! I have a series of png image files which are named movie001.png, movie002.png and so on. I would like to use these files as frames to create a video. SO far tried the following commands:

```

[COLOR=#555555][FONT=Monaco]ffmpeg -f image2 -r 06 -i *.png output.mp4[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]ffmpeg -i *.png -vcodec ffv1 -r 0.0001 test.avi
[/FONT][/COLOR]
```[COLOR=#555555][FONT=Monaco]

[/FONT][/COLOR]In both cases I manage to create a video file however the video was too short and so fast that the file got opened and closed immediately. In facts I could not see anything.
What am I doing wrong? Thanks a lot for your advice !!

---

### Post by SeijiSensei on 2013-09-07
Shouldn't the -r value be something like 24 to generate a video that displays at 24 frames per second?

---

### Post by scamiolo on 2013-09-08
Thanks for the reply. I have got 30 frames in total. Therefore I wrote a low value of r in order to have a longer video.
Any suggestion?

---

### Post by carl4926 on 2013-09-08
Why not just create a slideshow

---

### Post by evilsoup on 2013-09-08
```
ffmpeg -f image2 -r 6 -pattern_type glob -i '*.png' output.mp4
```

...should do it. You need to quote the *.png, otherwise the shell expands it into a list of all the png files in the current directory -- you don't want that, you want to pass a literal '*.png' to ffmpeg (which then internally expands that to every .png in the current directory...). You also need to use the '-pattern_type glob' option to make this syntax work, otherwise ffmpeg uses a different pattern-matching syntax.

---

### Post by scamiolo on 2013-09-08
thanks everybody! Evilsoup I tried your command and received the following error message:

```

ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Unrecognized option 'pattern_type'
Failed to set value 'glob' for option 'pattern_type'

```

Am I doing anything wrong?
thanks

---

### Post by evilsoup on 2013-09-09
No, I don't think you're doing anything wrong, it's just that ffmpeg (and avconv) is a fast-moving project, and the versions in the repositories are often out-of-date. It seems that the version you have doesn't have the '-pattern_type' option.

If the files are named after a pattern along the lines of 'img01.png, img02.png ... img30.png', then you should be able to use the following:

```
ffmpeg -f image2 -r 6 -i 'img%02d.png' output.mp4
```

'%02d' here means 'sequential numbers padded with two zeroes' (so 01, 02 ... 30, etc.).

---

### Post by coldraven on 2013-09-09
Fakeoutdoorsman posted this recently, it also adds sound. It's tailored for upload to Youtube.
```
ffmpeg -loop 1 -i image.png -i music.mp3 -c:a copy -c:v libx264 -crf 0 -s hd720 -preset veryslow -shortest output.mkv
```

---

### Post by shantiq on 2013-09-10
> **coldraven said:**
> Fakeoutdoorsman posted this recently, it also adds sound. It's tailored for upload to Youtube.
```
ffmpeg -loop 1 -i image.png -i music.mp3 -c:a copy -c:v libx264 -crf 0 -s hd720 -preset veryslow -shortest output.mkv
```



hmmm   that wonderful command for YT coldraven is really for 1 image and a sound file; what the asker wants here is multiple image and no mention of sound or YT
probably best he uses Esoup's command for this

---

### Post by FakeOutdoorsman on 2013-09-10
> **scamiolo said:**
> In both cases I manage to create a video file however the video was too short and so fast that the file got opened and closed immediately. In facts I could not see anything.

By default ffmpeg will use an input (and therefore the output too) frame rate of 25 frames per second. As evilsoup shows you can declare an input "-r" and it will use that value instead of the default. For example, if you want the input to be one frame every five seconds you can use a fraction: "-r 1/5". You can also use different values for the input and one for the output. This is useful if you want the output to vary from the input, such as if your video player can only handle "standard" frame rates. ffmpeg will simply duplicate or drop frames to match the difference.

```
ffmpeg -r 1/5 -i input -vcodec libx264 -pix_fmt yuv420p -r 25 output
```

Since your input is PNG, and therefore likely RGB, then "-pix_fmt yuv420p" will ensure your output is compatible with "dumb" players (QuickTime, WMP, etc).

> **scamiolo said:**
> thanks everybody! Evilsoup I tried your command and received the following error message:

```

*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Unrecognized option 'pattern_type'
Failed to set value 'glob' for option 'pattern_type'

```

I think I should clarify that ffmpeg (the original one) and avconv (and the temporary, old, fake, so-called "ffmpeg" in the repo) are tools from two different projects: FFmpeg and libav. The "deprecated" message is misleading for general users. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017) and [The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html).

As for "Unrecognized option 'pattern_type'", either use a non-ancient ffmpeg or use "ffmpeg -i movie%03d.png" instead of a glob pattern. You can follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide), or simply use a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) that you can download and use.

**Also see:**
[list]
[*][FFmpeg Wiki: FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)
[*][FFmpeg Wiki: Create a video slideshow from images](https://trac.ffmpeg.org/wiki/Create%20a%20video%20slideshow%20from%20images)
[*][FFmpeg FAQ: How do I encode single pictures into movies?](http://ffmpeg.org/faq.html#How-do-I-encode-single-pictures-into-movies_003f)
[/list]

---

### Post by scamiolo on 2013-09-12
Thanks evilsoup!! Your command worked perfectly!! And thanks everyone who added content to this thread!

---

