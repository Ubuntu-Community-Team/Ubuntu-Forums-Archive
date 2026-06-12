---
title: "Problem with wmv files"
date: 2010-03-26
forum: Multimedia Software
---

### Post by bullu on 2010-03-26
I have been trying to play a few WMV videos but the problem is that video is there but audio doesnot play when i tried to search for the plugin it says** windows media 9 decoder **not found.

i have tried to run the files in VLC but same problem no sound.
I found out that mplayer supports wmvs so i installed it but when trying to run the videos from mplayer nothing comes instead it says **error opening video_out(-vo) device** and cannot find codec for** audio format 0x162**

I'm using Ubuntu 9.10 karmic 64 bit...

---

### Post by mc4man on 2010-03-26
All wmv and wma can be decoded in 64 bit with the exception of wmal (lossless), though that's possible  thru installing a 32 bit mplayer

The repo mplayer is rather poor in this area, either use a ppa build (many available, or build yourself.

gstreamer now supports wma3(pro) - 0x162 - though only in lucid or thru the gstreamer-devs ppa for karmic 

vlc you'd need to build

gtsreamer ppa link and some more here
[http://ubuntuforums.org/showthread.php?p=8973387#post8973387](http://ubuntuforums.org/showthread.php?p=8973387#post8973387)

[build mplayer]("http://ubuntuforums.org/showthread.php?t=1305181")
[one of many mplayer ppa's]("https://launchpad.net/~rvm/+archive/mplaye")

screen shows the fairly crappy totem (gstreamer) playing a high bitrate wmv3 w/wmap audio in 64 bit and it does pretty well with it

---

### Post by bullu on 2010-03-26
Thnks for the suggestion but i found out that the files are WMV9 files so does it make a difference

---

### Post by mc4man on 2010-03-26
> files are WMV9 files so does it make a difference
Same difference - most are wmv3 w/ wmap audio
The only ones that are unplayable are drm'ed ones

For ex. all of these are playable (they are called wmv9 - see screen for what vlc (64 bit) reports - the adrenaline rush one in link

[http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx](http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx)

(for those curious - the samples dl as an .exe - they need to first  be unzipped thru opening in wine to a <whatever>.wmv

---

### Post by no2498 on 2010-03-26
mp3 is 263
mp4 is 264

smplayer can play the mp3's and mp4's

hope this helps

---

