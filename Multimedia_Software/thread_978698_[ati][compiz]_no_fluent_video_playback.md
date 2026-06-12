---
title: "[ati][compiz] no fluent video playback"
date: 2008-11-11
forum: Multimedia Software
---

### Post by zwaardmeester on 2008-11-11
Hi all, is it normal that the fullscreen video playback with (Normal) desktop effects enabled is not fluent? When i switch to metacity everything works fine. 

I have a few year old ati 9800pro videocard with proprietary drivers. Also tried the opensource drivers.

---

### Post by aeiah on 2008-11-11
probably not, but 1080p is rather demanding. what are your full system specs? it shouldnt be an issue since it works fine with metacity but its worth stating since HD content requires such high system specs.

what video player are you using? have you tried any others? in mplayer and xine you can set it to use GL for video drivers or whathaveyou, perhaps changing these has an affect?

---

### Post by Yashiro on 2008-11-11
Playing Video files:
- with the Ati Restricted Driver
- with Compiz running
- using the hardware overlay

Does not work correctly. 

To fix this you can:
-Go into Compiz options and toggle the unredirect output setting.
-Install Fusion-icon from the repository and switch between Metacity and Compiz more easily.


Yes, it sucks.

---

### Post by zwaardmeester on 2008-11-11
Thanks for the replies guys. Toggling the "unredirect fullscreen windows" setting did not help in my case. Playing the video in xine-ui with openGL also not. The video's I play are dvd and compressed avi, not HD. Videoplayers: totem (gstreamer, xine), vlc. 

I discovered that keeping the video player windowed and zooming in with "WIN-scroll" combination does result in fluently playing video. This is however not ideal for watching with subtitles. I think have to stick with the last option, switching between Metacity and Compiz. As many other problems with linux, they will disappear automatically over time ;)

---

