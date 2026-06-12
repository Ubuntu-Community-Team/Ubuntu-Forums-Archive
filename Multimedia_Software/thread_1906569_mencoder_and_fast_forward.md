---
title: "mencoder and fast forward"
date: 2012-01-09
forum: Multimedia Software
---

### Post by YustAnotherLinuxFriend on 2012-01-09
Hy everybody,

i recently bought an Panasonic DMP-BDT110EG Player and try 
to create avi files from my dvd collection. First thing i 
have to learn is that avi is no format, only the xvid format 
is running.

If i encode a dvd with the following line:

[FONT="Courier New"]mencoder  -dvd-device ${directory} dvd://1 
          -o ${directory}/${output} 
          -ovc xvid 
          -forceidx
          -oac copy 
          -xvidencopts pass=2:bitrate=2000 
          -vf scale=1366:768[/FONT]

I got an avi which is able to fast forward, but only until 
ca half of the movie. When i try to play, the picture freezes.
I have different running high resultion avi files which are
able to fast forward until the end of the film, from windows 
i would assume. So i think mencoder is the problem.

Are there any suggestions, what i can do better? Are there better
tools on linux? I use Ubuntu 64 10.04 

Many Thanks in advance

Dietmar

---

### Post by SeijiSensei on 2012-01-09
> **YustAnotherLinuxFriend said:**
> 
          -xvidencopts pass=2:bitrate=2000 
          -vf scale=1366:768

In order to do two-pass encoding you need to do, um, two passes!  See [this](http://en.gentoo-wiki.com/wiki/Mencoder#XviD_Two-Pass_Encoding) for details.

If your DVD player can handle MP4 files, I suggest using [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases") and converting to that format instead of AVI.  MP4 will let you use H.264 encoding instead of XviD.  Probably the most versatile container format these days is Matroska (.mkv), but commercial players generally don't support that.  If yours does, then I'd use Handbrake to encode to H.264 in the Matroska container with AAC or AC3 audio.

If you stick with the XviD/AVI combination, I'd recommend recoding the audio to MP3 as they do in the examples in that document.

---

