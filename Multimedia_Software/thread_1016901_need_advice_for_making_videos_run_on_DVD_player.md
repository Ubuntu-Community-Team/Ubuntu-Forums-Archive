---
title: "need advice for making videos run on DVD player"
date: 2008-12-20
forum: Multimedia Software
---

### Post by Stefan_xfce on 2008-12-20
Hi,
I have some video files that I want to see on my DivX-enabled DVD player. I can't play these files there, because they have either the "mkv" ("Matroska") extention or they are AVIs encoded with the "h264" codec, that my Philips dvd player cannot play.

Ok, so I found out, that I can easily use mencoder to transfer a variety of video formats to e.g. DivX.
The question is: which are the settings/switches, that would be best for my use to maintain the quality as much as possible?
I've already tried out several settings with changing success:

```
mencoder infile.avi -ovc xvid -oac mp3lame -xvidencopts bitrate=1500 -o outfile.avi
```
This works fine in most cases, but in some videos there's just an obvious quality loss.

```
mencoder <filename.avi> -ovc xvid -oac mp3lame -xvidencopts fixed_quant=3 -o <output.avi>
```
The visual quality of this output video is very good, but it sometimes stutters on my DVD player, (when there's lots of water bubbles or leaves e.g.), also it has no sound there, whereas on the computer it has.

So I was wondering if any of you guys ever had the same problems and found a perfect transcoding setting for the use on a DVD player.

Anyone?

Cheers,
 Stefan

---

