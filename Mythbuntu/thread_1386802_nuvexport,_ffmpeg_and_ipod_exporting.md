---
title: "nuvexport, ffmpeg and ipod exporting"
date: 2010-01-21
forum: Mythbuntu
---

### Post by vancheese on 2010-01-21
Hi 
I'm trying to export from my Karmic mythtv box to ipod compatitable formats.
I've tried installing mythexport but for some unknown reason its not working, So I've reverted back to using nuvexport.

Nuvexport works with mencoder (only xvid output) but its doesn't play with ffmpeg. I've recompiled ffmpeg from source ala [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) but nuvexport refuses to enable any useful options. 
ffmpeg seems to be compiled with all the right options(  --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab). The only difference is that 
the usual -vcodec=xvid has to be replaced by -vcodec=libxvid 

Everything else is from the main/medibuntu apt sources.

Are there any tests/suggestions for nuxexport to see these ffmpeg options 

Andy

---

### Post by FakeOutdoorsman on 2010-01-21
The nuvexport from the repository may be looking for a specific shared libavcodec soname (I believe that is the correct term) in */usr/lib*.  FFmpeg/libavcodec compiled from the guide you linked to is not shared and installs stuff to */usr/local/foo*.  *Disclaimer: I haven't actually tested any of this and I don't know anything about nuvexport.*

An easier option may be to use **libavcodec-extra-52** from the repository to enable additional encoders not present in **libavcodec52**.  If nuvexport uses AAC audio, then I recommend using the version of **libavcodec-extra-52** from the Medibuntu repository as explained here in *Option C*:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

