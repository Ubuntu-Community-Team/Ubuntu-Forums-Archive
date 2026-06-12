---
title: "Why do MP3 files sound better with VLC compared to Rhythembox and other programs?"
date: 2016-06-01
forum: Multimedia Software
---

### Post by jorrellian on 2016-06-01
Hi, I've noticed a slight distortion whenever I'd listen to my MP3 files on Ubuntu 16.04. I did some investigating and determined that VLC Media Player does not have distortion near any high notes in the music. I've used Rhythembox and Audacious. I cannot confirm if other applications also show this issue, however, this happens to those programs so far to my knowledge. I don't think this is a sound driver issue though, as I've played FLAC files and they sound just as they are supposed to across all programs, including other devices as well. I am under the impression that this is a codec issue. I would like to know if this is true and if there is any possibility in fixing this issue.

---

### Post by ajgreeny on 2016-06-01
Could this be the result of different default volume levels set in each application?

I use vlc a lot and audacious not quite as much, and both sound identical to me, but never use rhythmbox so I can't comment on that.

---

### Post by Yellow Pasque on 2016-06-01
For Rhythmbox, I would suggest uninstalling gstreamer1.0-fluendo package (if installed) and installing gstreamer1.0-plugins-ugly to see if there's a difference. The Fluendo mp3 codec is the best for legal/distribution purposes, but I have seen reports that it makes odd whistling noises on some mp3's

For Audacious, it is probably using the mpg123 plugin to play mp3's by default. You can try disabling it (select Output -> Effects in the menu and then look at the 'Input' tab) so that mp3's are decoded using the ffmpeg plugin, which should be the same thing VLC is using.

---

### Post by shantiq on 2016-06-02
So many factors probably explain why some players produce a better sound than others  ...
VLC always has had a great sound for me on my setup
Audacious too if I use File/Settings/Plugins/Effect/Crystalizer
But the best is still the old Swedish [XMMS]("http://ubuntuforums.org/showthread.php?t=2326649&p=13498646#post13498646") clear as a bell

I you have bat hearing :] you will appreciate that

Some players have way poorer sound
For me Clementine sadly has a slightly muffled/in the background  quality [can be improved with [Delta]("http://ubuntuforums.org/showthread.php?t=2257567&p=13192069#post13192069") plugin]
Deadbeef is ok but still feels a bit remote
Rhythmbox is the first piece of software i always delete :]

You can tinker with all of those and see if you can improve this or that one but to me clarity is paramount
so [XMMS]("http://ubuntuforums.org/showthread.php?t=2326649&p=13498646#post13498646") if you have the patience to install but VLC is always clear too

---

### Post by Yellow Pasque on 2016-06-02
shantiq, have you tried to use the ffmpeg plugin in Audacious?

---

### Post by jorrellian on 2016-06-02
I tried uninstalling the package and installing the one you told me. It did not make a difference with the audio quality. I also disabled the mpg123 plugin, but then it only decided to play my flac files instead.

---

### Post by jorrellian on 2016-06-02
I might try out XMMS as a last resort. Thank you.

---

### Post by mc4man on 2016-06-02
> **jorrellian said:**
>  I also disabled the mpg123 plugin, but then it only decided to play my flac files instead.
Doesn't sound right at all unless you've also disabled the ffmpeg plugin. Assuming "it" means audacious..

---

### Post by shantiq on 2016-06-02
> **Temüjin said:**
> shantiq, have you tried to use the ffmpeg plugin in Audacious?

yes T   it is always on  ...   Audacious is cool  ...   my second port of call always :]

---

### Post by Linuxisfast on 2016-06-03
Try with SMPLAYER, even better, install the mplayer latest via Doug McMahon PPA and SM Player via their ppa. Extra Stereo sound feature is just awesome. Also video color, CPU use far less compared to VLC.

---

