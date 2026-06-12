---
title: "how can i make MPlayer Movie Player play mp4 ?"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by DO55 on 2007-04-19
hi

i have mp4 video clip and also i have subtitled file (srt) , how can i make them played with MPlayer Movie Player ?

---

### Post by RomeReactor on 2007-04-19
Hi. Try this: Open Mplayer, right-click on it and select "Preferences"; on the "Video" tab choose **xv   X11/Xv** as the driver to use; on the "Codecs & demuxer" tab, choose **Null video decoder** or **FFmpeg's libavcodec codec family** as the "Video codec family, and **FFmpeg/libavcodec audio decoders** as the "Audio codec family"; click "OK", close Mplayer and open it again to see if you can  play that MP4 file now.

---

### Post by DO55 on 2007-04-19
WOW

thanks man !!!

---

