---
title: "Cantata / Audio Normalization"
date: 2018-03-13
forum: Multimedia Software
---

### Post by imaginashawn2 on 2018-03-13
I'm running Ubuntu 16.04 and a couple weeks ago I installed Cantata ver. 1.5.2 Using KDE dev platform 4.14.16
 I am very happy with Cantata but one thing that concerns me is I can't normalize the audio volume on my library of music leaving me to have to leap for the remote sometimes when the next song in the list is about to blow out my speakers. I've searched for info on normalization for the volume but to no avail. 
Can you help?

---

### Post by vanadium on 2018-03-14
Cantata is as I understand a client for the mpd music player. It is at the level of mpd that you need to enable replay gain. Edit your mpd config file and remove the comment from the line ```
replaygain			"auto"
``` (or add such a line). The mpd file explains the options.

For volume adjustment to actually work, your audio files must contain replaygain tags. These are tags that contain information on how the volume of the file should be adjusted in order to have a proper "reference" volume. A convenient command-line tool is provided by "replaygain" in the python-rgain package. That one can add replaygain tags to a range of audio formats (flac, ogg, mp3) and saves you from having to use a dedicated tool for each specific audio format.

---

