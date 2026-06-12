---
title: "Mplayer not playing stuff!"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by xardas on 2007-02-28
I've installed the Mplayer but it doesn't play any stuff such as mpeg, avi etc. It also doesn't play flv videos. There is some wierd error about io output something. I have downloaded the codecs and placed them in the /usr/lib/codecs directory. It contained all those dll files. What to do now?:(

---

### Post by RomeReactor on 2007-02-28
Hi. It looks to me like a driver issue. Open Mplayer and right-click on it, and select "Preferences". Then select the "Video" tab, and choose the **xv    X11/Xv** drivers; close Mplayer, open it again and try to play your files.

---

### Post by chriswyatt on 2007-02-28
Hi, I was also having the same problem.  I changed it to X11/Xv, the video now plays but during playback a message flashes on and off the screen really quickly saying:

alsa-control: unable to find simple control 'PCM',0

By the way, I have two soundcards, an HDA Intel and a USB Audigy 2 NX with the latter set as default, playback is through my USB soundcard.

---

### Post by RomeReactor on 2007-02-28
Try this: Open Mplayer, go to "Preferences --> Audio", select Alsa and click "Configure Driver". Set "Device" and "Mixer" to default; write "Analog Front,0" into Mixer Channel. Press OK on both windows, close Mplayer, open it again, and try to play a file.

---

### Post by xardas on 2007-03-01
Ok thanks. Mplayer is working now but there pops up an error dialog every time i play any file. Something about mp3 plugin not loaded or found or something. How can I remove that?

---

### Post by Datalanche on 2007-03-01
For the mplayer mp3lib error, I found this when I switched to edgy: "If you use GUI(gmplayer skin), go to Preferences, then click "codecs & demuxer". Select "FFmpeg....." for audio codec family. You may select ffmpeg for video codec family too!"

---

### Post by xardas on 2007-03-01
Thanks. That solved the proble. Another question, Whenever I open a media file it opens up in a new window. How can I make it open in the same Mplayer window?

---

### Post by panch0 on 2007-03-02
KPlayer is the KDE frontend for MPlayer that always plays videos in the same window. If you are on Kubuntu, definitely give it a try.

---

