---
title: "Distorted Video/No Subtitles in Mplayer, VLC, others"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by jesusfr3ak4evr on 2007-03-05
Alright, so I'm trying to play Fate-Stay Night (an anime) correctly in a media player. It is in H264 format, a .mkv file.

I have a Dell Latitude D600 with a Radeon 9000 32MB R250 FireGL video card and the latest drivers for everything.

In Mplayer, I get perfect audio and video, but cannot select a subtitles track. The subtitles are in both .srt and .*** format. I know this from VLC.

In VLC, the video is distorted. I tried changing my screen resolution and using SDL and X11 video outputs, but that made no difference. I don't know where I can change the screen depth, so I didn't try that. Any ideas on where I can do this? I'm using Ubuntu LTS 6.06

In Movie Player/Kaffeine/Xine, I get everything working right except the audio chops every 5-10 seconds or so. It's viewable, but really gets annoying. 

Any ideas from anyone on fixing this? I also get distorted video in both VLC/Mplayer for One Piece, another H264 video file.

---

### Post by RomeReactor on 2007-03-05
Hi. Sorry i can't help you with most problems, but regarding the subtitles, make sure the .srt file is named **exactly** like the .mkv; it should load automatically in Mplayer then.

---

### Post by jesusfr3ak4evr on 2007-03-05
Regarding the subtitles... they are not in a separate file from the video. In VLC I can select between either .srt or .as(s) for subtitles. I don't understand why the subtitles do not load automatically in Mplayer. There is no option anywhere in the program to select subtitles either. At least, none that show any available subtitles.

---

### Post by panch0 on 2007-03-07
KPlayer uses MPlayer behind the scenes, so that should be your best bet. If the subtitles don't show up automatically, there is a Subtitles submenu under Player where you can select embedded subtitles. For external subtitles there is File - Load Subtitles.

---

### Post by stulesnett on 2007-03-07
Hi,
I'm running Ubuntu 6.06 after recent systems update Mplayer stopped displaying movies and sound.  A quick window will open the screen and disappear but no errors.  The same thing happens when I try to execute the standalone application.

Then after saving the wmv I try to use frostwire to executive the movie and receive a window indicating an err. but then the sound starts to play (NO Pucture).

Error: Couldnot open required DirectShow codec wv9dmod.dll

Any help would be appreciated.

Stu

---

### Post by panch0 on 2007-03-07
Please post the full output MPlayer gives you.

---

### Post by surfjdh on 2007-04-10
in mplayer press "j" to toggle between subtitles, mkv and linux is a bit*h.

---

