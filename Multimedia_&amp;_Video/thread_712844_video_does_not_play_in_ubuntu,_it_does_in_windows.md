---
title: "video does not play in ubuntu, it does in windows"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by Jean__ on 2008-03-02
Hello,

After 4 months in ubuntu I switched back to windows this morning. I have a large video database, mostly real media files. There are movies that ubuntu does not play well, at a certain point the player just hangs. I tried, mplayer, smplayer, xine, totem, vlc, real player, I tried to change video options a bit in mplayer, but still those video's crash, and sometimes badly, I have to kill the process.

In windows, zoom player, it just plays. This is important enough for me to switch back though I am really sad about it.

So if there are options I could try, please let me know.

Thanks, Jean.

---

### Post by gandaran on 2008-03-02
the best linux player to handle real video is gxine, it'll play most formats, for me it fails only on some avi files.
totem gstreamer will play the other files gxine won't.
for totem gstreamer, install all the gstreamer plugins, the bad, good and ugly.
for gxine install libxine1-ffmpeg, w32codecs, libdvdcss2, libdvdnav4, and libdvdread3
with these two players and all codecs installed, your ubuntu should handle any media format.

---

### Post by Jean__ on 2008-03-02
Thanks.

I tried gxine, same result however. There is a point 5 minutes into the video where the players just give up. 
:(

---

### Post by gandaran on 2008-03-02
maybe this problem is related to the video card, 
what make is your video card and which driver you are using?
are you using compiz?

---

### Post by Jean__ on 2008-03-02
No compiz please. :) 
First try to get things working as they should. 

I have an nvidia 7600 GT, I use it in windows to play rally games, and it's working ok for me. I have the nvidia driver in ubuntu set up ok, I watch my movies on tv with separate x screens.

So no, I don't think it's the video card. 

Well I spent one hour in windows this morning, trying to get qdevelop/qt working there, but had no luck and I missed my ubuntu so I already settled for some video's not working.
But when I got your answer, I got an idead and tried to play that file from the local harddisk in stead of over the network and yesss, no more crashes.

So the culprit is buffering over the network somehow.

Btw I uninstalled gxine, I had problems with it, it did not quit and the process hang.

So maybe I'll find a solution for the network issue, maybe increase buffer size or something.

Thanks for your time.
Jean.

---

### Post by andrew.46 on 2008-03-05
Hi,

 Perhaps you could install the svn mplayer with a full codec pack:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

 This should play almost all video formats although it has the risk of being potentially unstable.

          Andrew

---

### Post by sarah.love on 2008-03-05
> **gandaran said:**
> the best linux player to handle real video is gxine, it'll play most formats, for me it fails only on some avi files.
totem gstreamer will play the other files gxine won't.
for totem gstreamer, install all the gstreamer plugins, the bad, good and ugly.
for gxine install libxine1-ffmpeg, w32codecs, libdvdcss2, libdvdnav4, and libdvdread3
with these two players and all codecs installed, your ubuntu should handle any media format.

NEW USER: - how do you install libxne1-ffmpeg etc etc....where do you go/what do you do to install these?

---

### Post by 6205 on 2008-03-05
> **Jean__ said:**
> Hello,

After 4 months in ubuntu I switched back to windows this morning. I have a large video database, mostly real media files. There are movies that ubuntu does not play well, at a certain point the player just hangs. I tried, mplayer, smplayer, xine, totem, vlc, real player, I tried to change video options a bit in mplayer, but still those video's crash, and sometimes badly, I have to kill the process.

In windows, zoom player, it just plays. This is important enough for me to switch back though I am really sad about it.

So if there are options I could try, please let me know.

Thanks, Jean.

WOW....now when i asume that you don't have corrupted system and Real Player is working i don't understand anymore sense of this lame player anymore if it doesn't play even his own files :confused:

---

### Post by Misbah on 2008-03-07
Ubuntu has never supported RM or RA properly, streaming or otherwise. It sucks.

---

