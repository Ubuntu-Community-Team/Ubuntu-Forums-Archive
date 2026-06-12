---
title: "Converting DVD Rip with MakeMKV to Ps3 Format and Keep Subtitles?"
date: 2013-06-19
forum: Multimedia Software
---

### Post by mamamia88 on 2013-06-19
I was wondering what the best way to convert an mkv ripped with makemkv to a ps3 playable format and keep subtitles that can be toggled?

---

### Post by SeijiSensei on 2013-06-19
Rather than converting the files, you could run [ps3mediaserver]("http://www.ps3mediaserver.org/") on the Ubuntu box, then connect to it from the PS3 using the DLNA protocol that it supports natively.  It should do the conversions on-the-fly.  I don't know about how it handles soft subtitles, though.

Natively the PS3 does not support Matroska.  The only supported container that handles subs is MP4.  [Handbrake]("http://handbrake.fr/") can convert to that format and preserve the subtitles.  If you want to use Handbrake, follow the instructions on [this page]("https://launchpad.net/~stebbins/+archive/handbrake-releases") to add the repository for Ubuntu.  

If you are willing to have "hard" subtitles, ones burnt into the video image, you can convert to XviD+MP3 in the AVI container with ffmpeg or mencoder.

---

### Post by mamamia88 on 2013-06-19
Handbrake can preserve the subtitles and have them optional on ps3?  I thought that it only worked with forced subtitles?  I also tried media server before but i'm on wifi and far away from router so i prefer a native format.    It would be awefully nice to rip my dvds and have them on the harddrive.

---

