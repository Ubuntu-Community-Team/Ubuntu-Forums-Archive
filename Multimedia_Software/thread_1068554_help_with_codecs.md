---
title: "help with codecs"
date: 2009-02-13
forum: Multimedia Software
---

### Post by anand1712 on 2009-02-13
I have a big of collection of movies obtained over a long period.

Many of them are in formats like Divx,xvid,mp4 etc etc.

I want to convert all to a standard format so that all files are similar.

Can you suggest me the best possible codecs for video and audio.I want to retain the same quality in video and audio but have a common codec for all so that it is easy to maintain.


Also is there any app in ubuntu which will give you the details of the codecs of the file which have been used.

---

### Post by Hellkeepa on 2009-02-13
HELLo!

The best option, for maintaining quality, is to leave them as they are. By transcoding you will reduce the quality even more, unless you store the files in a lossless format. Something which will bloat the files to incredible sizes, without giving you any improvement in quality at all; An 700 MB DivX 3.0 file will still look like one, while taking up several GB of HDD space.

If you still want to transcode them, I can recommend the MKV container, using x264 for the video codec and FLAC/AAC for the audio. That'll retain the quality as much as possible, if you configure it correctly[1], without growing the files too much.
Also hope you got a lot of time on your hands, because transcoding the videos will take several hours per movie, depending upon the quality you want.

As for what applications to use: I find that mencoder & mplayer can do most stuff for you, for those pesky VMW9 movies, however, you might want to install AVIsynth (windows only).

[1] This is a science, and I recommend reading a *lot* up on this subject before you start to automate this task!

Happy codin'!

---

### Post by ouija on 2009-02-13
That seems a bit tedious but I would suggest the format that is most compatible with all of your players, and only convert the ones that are incompatible with any of your systems.  DivX would be my suggestion..

As for identifying the codecs used in almost every type of media file, I would suggest using media info,

Download package for mediainfo (use debian) --> [http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612&release_id=657286](http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612&release_id=657286)

Download required addons (use ubuntu files) --> [http://mediainfo.sourceforge.net/lt/Download](http://mediainfo.sourceforge.net/lt/Download)
get both for Ubuntu.

install libzen0 first, then libmediainfo0 then install the mediainfo package.

after installation, simply open the terminal and type "mediainfo filename.ext" to output the media file info.

---

### Post by cb951303 on 2009-02-13
I would suggest Theora for video compression and Vorbis for audio compression. *.OGV as the container file format.
all open source formats/codecs:popcorn:

---

