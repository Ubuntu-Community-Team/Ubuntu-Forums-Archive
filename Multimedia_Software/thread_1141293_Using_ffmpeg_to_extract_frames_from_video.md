---
title: "Using ffmpeg to extract frames from video"
date: 2009-04-28
forum: Multimedia Software
---

### Post by SillySod on 2009-04-28
I know I can use ffmpeg to extract all the frames of a video file as separate images, such as:

```

ffmpeg -i Video.mpg Pictures%d.jpg

```

Is there a way I can use this to create an image every, say, 50 or 75 frames?  If I extract every frame there will be too many to use.

---

### Post by lovinglinux on 2009-04-28
If you want to generate a contact sheet, you can use  [Video Contact Sheet *NIX (vcs)](http://p.outlyer.net/vcs/). Is just a script, so if open it with a text editor you might find the code to do what you want in the command-line.

---

### Post by cipi.ro on 2009-10-02
Hi,

Look here: [http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-November/005327.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-November/005327.html)

It says to do something like:

```

# ffmpeg -i file.mp4 -y -ss 5 -an -sameq -f image2 -r 1/5 filename%03d.jpg

```

I did some research on all the options involved in the command above:

-y
[INDENT]Overwrite output files[/INDENT]
-ss position
[INDENT]Seek to given time position in seconds. "hh:mm:ss[.xxx]" syntax is also supported[/INDENT]
-an
[INDENT]Disable audio recording[/INDENT]
-sameq
[INDENT]Use same video quality as source[/INDENT]
-f fmt
[INDENT]Force format[/INDENT]
-r fps
[INDENT]Set frame rate (Hz value, fraction or abbreviation), (default = 25)[/INDENT]


This means that the command could be simplified to:

```

# ffmpeg -i file.mp4 -r 1/5 filename%03d.jpg

```

Maybe you might want to use -ss too.
Also, I think that - r 1/5 result from the fact that you have a video at 25 fps and you want to grab frames with a 5 seconds step (25 * (1/5) = 5)

---

