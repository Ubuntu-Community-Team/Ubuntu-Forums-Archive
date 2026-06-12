---
title: "video playback is b&amp;w and dvds are blocky?"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by wtfdoyouwantdude on 2008-02-19
what do i do. my mpegs, avis, wmvs, all playback in b&w. also, my dvds are all blocky. whats causing this? HELP!!!!!!

---

### Post by Aquaman420 on 2008-02-19
Depending on what player you are using, you might need to change the video output in the players preferences and then restart the player.  Post back with what player you are using and if you installed libcss2 and someone will be able to help you.

---

### Post by Aquaman420 on 2008-02-19
If you don't have libcss2 or have no idea what I am talking about here is a thread that will help you

[http://ubuntuforums.org/showthread.php?t=700953&highlight=install+codecs]("http://ubuntuforums.org/showthread.php?t=700953&highlight=install+codecs")

---

### Post by wtfdoyouwantdude on 2008-02-19
it happens in all 3 players, vlc, movie player, and mplayer.

---

### Post by Aquaman420 on 2008-02-19
Do you have the libdvdcc2 ,libdvdread3 installed.  If not that is for sure the problem.  That post I gave earlier explains how to get them, but if you get lost report back and myself or someone else can help you.

---

### Post by wtfdoyouwantdude on 2008-02-19
i did the install and xine player works great. now i have another issue. some of these files arent playing all the way through, but they did in winblows. any ideas... im sure its codec related.

---

### Post by Aquaman420 on 2008-02-20
Not playing all the way through huh?  That is a little strange.  You mean like you are watching it and it just quits on you?  I really haven't encountered that issue.  I would recommend installing totem-gstreamer and some of the other gstreamer packages if you haven't done so. JUust cut and paste this into the terminal.  Don't worry if you have some of these already, it will skip the ones you have.  totem-gstreamer will replace totem-xine.  I had some weird media problems for a bit using the xine libraries and installing this stuff fixed it.  It might do the same for you.  I On the plus side the gstreamer library replaces a video icon with a frame from the video and looks cool! I use SMplayer for all my video playback.  It is found in the repos.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mpegdemux gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-tools gstreamer0.10-x gstreamer-tools totem-gstreamer
```

---

