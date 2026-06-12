---
title: "Problem with videos in Creative Zen Vision W"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by freakanth on 2007-06-13
I use Ubuntu 7.04 on my system. Recently I purchased a Creative Zen Vision W portable media device. The problem I have is that it plays only some of the avi files that I have correctly (while it's supposed to play all avi files). It doesn't play the video in most cases and in some, it's the audio. Since these movies that I tried playing were downloaded from the internet, I figured there was a problem in the encoding. So I re-encoded the videos first using mencoder and when that didn't work, ffmpeg. I used mpeg4 for video and mp2 for audio encoding (since ffmpeg said that it didn't recognize mp3 :shock:). Alas, it still didn't work. Could someone please tell me how I can get these video to play on my player. I don't have windows on my PC so I can't use the creative support CD that was given with the player (and apparently it takes several hours for even the software to convert the files into the supported format so I guess I won't be using it anyway)

Srikanth

---

### Post by Jubalgunn on 2007-06-13
I tend to use video files that  have been  converted from dvd into xvid format. Xvid's always work with the zen. I have used ffmpeg without too much of a problem.
I have started using a macosx program that is open source- called Media Fork [http://www.macupdate.com/info.php/id/24032](http://www.macupdate.com/info.php/id/24032). This is awesome for converting DVD's and allows you to convert to several different formats. 
DVD RIP is also a favorite of mine and can convert dvd's to xvid/ avi format which play very nicely on the zen.
The ZEN will not play mpeg4 format video files (e,g commonly associated with quicktime and ipods.)
I personally prefer the xvid format . i also advice for the best dvd conversions try for a file size of 700mb to 1gb max. DVD rip does some nice xvids at arounf 700 mb.
Mediafork on the Mac is the quickest I have used .
:)
Another program that I use is called SUPER [http://www.erightsoft.com/SUPER.html](http://www.erightsoft.com/SUPER.html). This is good for converting video files of almost any format to another format. Its free as well . :)

---

### Post by freakanth on 2007-06-19
Hey thanks for the suggestions man. Super was for windows so I didn't use it. Didn't get to use media fork either. However, this is what I did using mencoder.

mencoder -ovc xvid -oac copy -xvidencopts bitrate=687 -o <output.avi> <input.avi>

I just changed the output video codec (ovc) and using the same audio codec (oac) for output as the input because I had a problem only with the video format. In case you have  a problem with the audio format too, you can give 'mp3lame' as an argument in place of 'copy' (I haven't tried but it should work :) ).

There's more on video/audio encoding using mencoder on this link:\

[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

---

