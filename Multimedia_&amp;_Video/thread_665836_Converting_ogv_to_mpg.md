---
title: "Converting ogv to mpg"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by Ederico on 2008-01-12
Hello,

Can anyone instruct me on how to convert a file from an .ogv format to an .mpg format? Thanks for any help granted.

Ederico.

---

### Post by polmir on 2008-01-12
[http://en.wikipedia.org/wiki/Ogg]("http://en.wikipedia.org/wiki/Ogg")
[http://en.wikipedia.org/wiki/Comparison_of_container_formats]("http://en.wikipedia.org/wiki/Comparison_of_container_formats")

---

### Post by Ederico on 2008-01-12
I found nothing on how to convert there, or am I missing it?

---

### Post by ron999 on 2008-01-12
Hi
I don't think those links will explain to you how to convert that file.
The links explain that ogv is a container with an audio file and a video file inside, and which codecs are probably used.

Maybe someone will come along with a command-line instruction for you using mencoder or ffmpeg.

---

### Post by Ederico on 2008-01-12
I managed on my own! Found the code on this site, luckily I recognised the code as that language (Portuguese I assume) is one that I do not know.

Code was this ```
mencoder -idx input.ogv -ovc lavc -oac mp3lame -o output.avi
```

Now I'd need the code so that I perhaps compress the output.avi further, it is a question of dimensions so I wouldn't mind changing the format (unless quality is substantially affected).

---

### Post by ron999 on 2008-01-12
Yes, you're making progress.:-D

I think that you could use ffmpeg instead if you wish, like this:-

> ffmpeg -i input.ogv output.mpg

And if you want to improve it type **ffmpeg -h** into the monitor for options.

:guitar:

---

### Post by Ederico on 2008-01-12
> **ron999 said:**
> Yes, you're making progress.:-D

I think that you could use ffmpeg instead if you wish, like this:-



And if you want to improve it type **ffmpeg -h** into the monitor for options.

:guitar:

That didn't work as I tested it out, at the end of the text in the terminal I got the following:

```
[mpeg1video @ 0xb7e53ac8]MPEG1/2 does not support 15/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by ron999 on 2008-01-12
OK, my bad.
Perhaps it's best to convert it to avi as you have done.
```
ffmpeg -i input.ogv output.avi
```

And if that's no good, stay with your **mencode**r command.
8-)

---

