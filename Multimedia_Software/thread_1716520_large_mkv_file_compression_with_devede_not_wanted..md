---
title: "large mkv file compression with devede not wanted...."
date: 2011-03-28
forum: Multimedia Software
---

### Post by adduds on 2011-03-28
1. just wondering when i take my 6.8gb.mkv file throw it through devede and assuming im getting compression because i end up with like a 3 something gig file is there a way i can take a large mkv make an iso file system to play on a dvd player i've read lots about this

2. K3B if i select video cd and use my 6.8gb.mkv file and burn that will it work in a standard dvd player?

correction i went from 6.9 to 1.6 video still looks good but i probably lost lots of quality?

---

### Post by SeijiSensei on 2011-03-28
DeVeDe has a [known bug]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/349011") where it's unable to determine the size of the resulting file when it uses MKV as a source. Typically it vastly over-estimates the actual size that the file will consume on the DVD.  There are ways around this, such as specifying the output bitrate explicitly, but it takes some playing around to get a good result.  Last time I used it, I created three or four test .iso's until I found the right bitrate to ensure all the files would fit at the best quality.

You probably haven't created a degraded ISO at all.

---

### Post by adduds on 2011-03-28
genisoimage -allow-limited-size -udf -o trial The\ Tourist_subs_test.mkv

i tried doing that as it kept original file size but when i burnt the dvd and put it into my computer it just opened up and showed The Tourist.mkv file within so did that procedure just create a iso "bubble" around the file? which was still inside

that first video i made with devede looks great on my hd tv through my blu ray player :)

just that if its only a 1.6gb file and i'm using a 4.7gb disc it seems wasteful to loose that space; along with the bandwidth considering i download a 6.8gb file and end up with a 1.6...but i guess you could say if i started with a 1.6 devede'd it i'd end up with some still substantially smaller

forexample if i have two files (mkv) maybe ones 4.4 gb and another 6.8 but they both end up (together) below 4.7gb with devede i'm left with two iso's but stuck burning two seperate discs? is this right?

i have :

Avidemux (GTK+)
Brasero
mkvmerge GUI
k3b
devede

aswell as the mkvdts2ac3 script installed

---

### Post by adduds on 2011-03-28
> **SeijiSensei said:**
> DeVeDe has a [known bug]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/349011") where it's unable to determine the size of the resulting file when it uses MKV as a source. Typically it vastly over-estimates the actual size that the file will consume on the DVD.  There are ways around this, such as specifying the output bitrate explicitly, but it takes some playing around to get a good result.  Last time I used it, I created three or four test .iso's until I found the right bitrate to ensure all the files would fit at the best quality.
You probably haven't created a degraded ISO at all.

oh so would that be under advanced options and video rate kib/s? it was set at 5001 so playing with that will increase size and maybe a lil quality?

thanks seijisensai you're always so helpful! i hope someday i'm knowledgeable like you so i too can help people

---

### Post by GWBouge on 2011-03-28
> **adduds said:**
> just that if its only a 1.6gb file and i'm using a 4.7gb disc it seems wasteful to loose that space; along with the bandwidth considering i download a 6.8gb file and end up with a 1.6...but i guess you could say if i started with a 1.6 devede'd it i'd end up with some still substantially smaller

forexample if i have two files (mkv) maybe ones 4.4 gb and another 6.8 but they both end up (together) below 4.7gb with devede i'm left with two iso's but stuck burning two seperate discs? is this right?

I agree that it seems like a waste of space, but I've used DeVeDe in the past to create DVD's of various video files (from 1GB to 15GB), and even though the output iso always ends up a bit smaller than the original (even if I started with a 4GB file and ended up with a 2GB iso), I haven't really noticed a considerable difference in quality considering the size difference.  Perhaps it's just a result of going from an .mkv to a DVD's standard .VOB format?

You can use mkvmerge to append one file to another one.  Just 'Add' the first video, and 'append' the second one, and it will create a single video file.  You can also (I'm pretty sure?) use the ffmpeg or cat commands to do this, but I'm unsure of the syntax and options available, so it would take a bit of playing around to get right, when you can just do a few clicks on mkvmerge to do the same thing (with certain video/audio formats, at least).

---

### Post by adduds on 2011-03-29
> **SeijiSensei said:**
> DeVeDe has a [known bug]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/349011") where it's unable to determine the size of the resulting file when it uses MKV as a source. Typically it vastly over-estimates the actual size that the file will consume on the DVD.  There are ways around this, such as specifying the output bitrate explicitly, but it takes some playing around to get a good result.  Last time I used it, I created three or four test .iso's until I found the right bitrate to ensure all the files would fit at the best quality.

You probably haven't created a degraded ISO at all.

What option is this in DVD to specify the output bitrate?

Creating these takes about an hr so it's really really annoying

I'd like to use mencoder but man using that in cli looks really really hard i've done some quick read overs and its like you gotta know EVERYTHING about a video, channels, audio, interlacing etc.....

---

### Post by SeijiSensei on 2011-03-29
> **adduds said:**
> What option is this in DVD to specify the output bitrate?

Click the video tab on the main screen, then the "bitrate" radio button.  The numeric bitrate control will then activate.  Mine shows a default of 1500.

---

### Post by adduds on 2011-03-29
DeVeDe doesn't have that on its main screen....?

---

### Post by SeijiSensei on 2011-03-29
Sorry, my mistake.  For some reason I was looking at Handbrake!  Guess I was trying to do too many things at once.

It's in the File Properties dialog.  Add a file, then choose the Advanced options beneath the Subtitles area.  You'll see the video and audio bitrates DeVeDe proposes to use in the General tab. I gave it a couple of different MKV's to try; I get 5001 as the video bitrate and 224 for audio in each case.  As I recall I got these values before with a different Matroska file.  They must be the defaults if the container doesn't include bitrates.  In those circumstances, the technique described in the [final posting]("https://bugs.launchpad.net/ubuntu/+source/devede/+bug/349011/comments/15") of the bug report gives you a method of determining the bitrate of the source material using mencoder.

---

### Post by adduds on 2011-03-29
```
The.Tourist.2010.BluRay.720p.x264.DTS-MySiLU
[lavf] stream 1: audio (dca), -aid 0, -alang eng
[lavf] stream 2: audio (ac3), -aid 1, -alang eng
VIDEO:  [H264]  1280x534  0bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:1280x534  fps:24.000  ftime:=0.0417
videocodec: framecopy (1280x534 0bpp fourcc=34363248)
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing index...81f ( 2%) 2872.38fps Trem:   0min 3056mb  A-V:0.000 [4379:0]
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
[B][U]
Video stream: 4379.665 kbit/s[/U][/B]  (547458 B/s)  size: 65717785 bytes  120.042 secs  2881 frames

```

wow where do you find all this stuff man that's amazing i used that it worked; but the video stream is 700 short making the file smaller? well i guess for now i guess i'll leave this as a mystery lol and just be happy i can burn pretty decent quality mkv's

i just don't understand it and it bugs me that 2.5 gigs of data dissapears....i read the bugs posts and that's the file i'm having trouble with is a x264 encoded file

---

