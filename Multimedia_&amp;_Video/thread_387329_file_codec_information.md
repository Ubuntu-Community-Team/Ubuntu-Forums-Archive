---
title: "file codec information"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by andytof47 on 2007-03-18
Hi I have a file that is in AVI format and have all the usual codecs installed in my edgy box however this NORBIT file won't play - it has a win32 installer but I tried this on my windows box and it didn't work


What I want is to find out the information on the codecs that this file is using - there is a program in windows that does this is there one for linux that will give the info?

---

### Post by chewearn on 2007-03-18
I have also been looking for such program in Linux.  Unfortunately, I don't think it exist.  In Windows, there is the "GSpot Codec Information Appliance"; which I have been able to run successfully using Wine (though it looks absolutely awful).
[http://www.headbands.com/gspot/](http://www.headbands.com/gspot/)

---

### Post by yabbadabbadont on 2007-03-18
The idvid script that is part of tovid (search the forums for the tovid howto) will identify videos.  It uses mplayer I think to do this.  I also believe that ffmpeg and transcode each have ways they can be used to identify the video codec and sound type in a video.

---

### Post by yabbadabbadont on 2007-03-18
If you have ffmpeg installed, just run "ffmpeg -i videofilename" and it will spit out the information about the file including the video and sound formats.

---

### Post by andytof47 on 2007-03-18
Hey thanks for the ffmpeg -i command...... no luck with the codec info though :confused: 

not to worry just go to the cinema or DVD shop if I really want to see it ------ but I don't:)

---

