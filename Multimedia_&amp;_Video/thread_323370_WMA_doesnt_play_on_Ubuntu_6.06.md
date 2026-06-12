---
title: "WMA doesnt play on Ubuntu 6.06"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by akshay_jp on 2006-12-22
Hello guys...

I installed the w32codecs but i am not able to play wma in XMMS or Beep Media Player.... It plays in mplayer and VLC perfectly alright...

when i load the wma file in the playlist in BMP , XMMS... they just quit... i dunno whats wrong...

it wud be great if u cud tell what is the problem... and possibly the solution...

thanks n regards...
akshay

---

### Post by aidanr on 2006-12-22
according to the bmp faq page, wma playback needs gstreamer-ffmpeg
so try in a terminal "sudo apt-get install gstreamer0.10-ffmpeg"

---

