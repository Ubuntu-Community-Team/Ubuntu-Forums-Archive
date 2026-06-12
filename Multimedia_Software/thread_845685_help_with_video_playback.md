---
title: "help with video playback"
date: 2008-06-30
forum: Multimedia Software
---

### Post by chillyair on 2008-06-30
recieved this message when trying to play a avi in totem

"The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed."

and i got this message trying to play the same one in mplayer

"cannot find codec for audio format 0x163"


can anyone help

---

### Post by edm1 on 2008-06-30
It appears you dont have the correct gstreamer packages necessary to play the file. The best thing to do however, is to in Video Lan Player and not worry about codecs ever again. Clicking this link should install it for you: [install vlc]("apt:vlc").

If you did want the gstreamer plugin so that you can continue using totem: [install gstreamer0.10-ffmpeg]("apt:gstreamer0.10-ffmpeg").

---

### Post by chillyair on 2008-06-30
> **edm1 said:**
> It appears you dont have the correct gstreamer packages necessary to play the file. The best thing to do however, is to in Video Lan Player and not worry about codecs ever again. Clicking this link should install it for you: [install vlc]("apt:vlc")

I already have vlc installed. However when I try to open that movie with it, the program starts and I get no error message but the movie just doesnt play.

---

### Post by markbuntu on 2008-06-30
You need to get the codecs from medibuntu.

You can do that by following the Multimedia guide at the top of this forum.

---

### Post by mc4man on 2008-06-30
> audio format 0x163 that's wma lossless, try 
```
sudo apt-get install w32codecs
```
(assuming you have medibuntu repo's in your software sources. I don't have any  wma lossless so can't say if they're playable or not
Edit; Quick test w/lossless - mplayer works fine as does totem-xine, vlc doesn't.

---

