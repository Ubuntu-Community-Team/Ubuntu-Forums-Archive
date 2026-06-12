---
title: "Saving Streaming WMV Video"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by rykel on 2007-04-28
Hi,

I am sure this question has been asked many times... if so, could you please direct me to the right threads?

Anyway, I wonder how I can save streaming Windows Media Player videos in Ubuntu?

One of the sites I need to visit frequently is viewable only in Windows, and when the Firefox/Totem-xine plugin tries to play the videos, it just stops. Nothing happens.

Therefore, I reckoned that the best thing to do is to save the entire video to my hard disk for viewing within the standalone Totem.

Thanks for helping!

---

### Post by chmac on 2008-03-07
[This post has a detailed explanation]("http://www.linuxquestions.org/questions/linux-general-1/mplayer-and-mencoder-the-dvdmovievideomp3-player-and-encoder-for-linux-616681/"). Here's the summary:

> 1) mencoder mms://address.of.site/movie.wmv -ovc copy -oac copy -o output.avi
2) mencoder rtsp://address.of.site/movie.wmv -ovc copy -oac copy -o output.avi
3) mencoder movie.wmv -ovc lavc -lavcopts vcodec=msmpeg4:vbitrate=750:vhq -oac mp3lame -o output.avi
4) mencoder dvd://1 -aid 129 -oac mp3lame -lameopts br=48:cbr:vol=6 -ovc frameno -o frameno.avi
5) mencoder movie.wmv -ovc copy -ofps 24000/1001 -oac mp3lame -of mpeg -o output.mpg

The above commands do the following (in order):

1) save an MMS video stream to the file output.avi (AVI is the default format).
2) save an RTSP video stream to the file output.avi.
3) encode WMV video as MPEG4 video with MP3 audio.
4) rip the German audio stream from a DVD and save it as an "MP3 video" labeled by frame number.
5) change the WMV file from AVI format to MPEG format with MP3 audio.

---

### Post by Ba|der on 2008-04-09
I wonder if it's possible to download some movies where I have broadband access for offline viewing. Like Video On Demand from [http://www.classicsfree.tv/](http://www.classicsfree.tv/) It's first a html  protocol with .mov extensions (small tiny file, with rtsp protol and mp4 extension). I've tried some of the tips with mplayer, vlc and mencoder but if the program not crashed with segmentation fault it just gave a file with no video.

---

### Post by chmac on 2008-04-09
I found that mencoder did work for me, although it did crash during download a few times, but I was in South Africa on slow internet. I'm going to try again in Thailand and see if it works better here.

---

