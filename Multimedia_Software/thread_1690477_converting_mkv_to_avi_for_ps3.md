---
title: "converting mkv to avi for ps3"
date: 2011-02-18
forum: Multimedia Software
---

### Post by gregcoit on 2011-02-18
Hi all,

I have mediatomb (0.12.0~svn2018-6ubuntu2) installed on Ubuntu Server 10.04.2 LTS which I use to serve video to my PS3 (slim version).  MOst videos work fine but I have some mkv's giving me trouble.

I'm trying to use mencoder to re-code the video to one that the PS3 can play.  

mkvinfo says the video track is Codec ID: V_MPEG4/ISO/AVC and the audio track is Codec ID: A_AC3.

I used this command to convert to avi (found it in a thread on this forum):

mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 video.mkv -o video.avi

but the PS3 says the avi is an unsupported format.  Any ideas?

Thanks!

Greg

---

### Post by Jose Catre-Vandis on 2011-02-18
You may have to demux the video and audio tracks, encode each then remux. Try just encoding some of the video and see if that works, this should then tell you its the ac3 audio that is causing the problem?

```
ffmpeg -i video.mkv -an -t 100 -vcodec libxvid -vtag XVID videoonly.avi
```

or try out WinFF?

---

### Post by inobe on 2011-02-18
i know someone that used DeVeDe to create a divx file that was playable from media tomb, the file could also be burned as a data dvd and be playable on home players and ps3.

[http://www.files.majorsilence.com/devede/docs/select.html](http://www.files.majorsilence.com/devede/docs/select.html)

the ps3 is divx compliant, if you noticed, you can work with mkv's and maintain their high def resolution converting to divx.

---

### Post by coffeecat on 2011-02-18
> **inobe said:**
> i know someone that used DeVeDe to create a divx file that was playable from media tomb

DeVeDe is what I use to prepare AVIs for playing on my PS3, except that I transfer them to the PS3 internal drive.

Choose the last option - DivX/MPEG-4 - from the first window when DeVeDe first opens.

---

### Post by gregcoit on 2011-02-18
Thanks everyone - I'll try these ideas and report back!

Greg

---

### Post by inobe on 2011-02-18
i left out something, for anyone that wants to use it on home players, these players have to be able to support divx!

all other settings will most likely work on all players.

---

### Post by gregcoit on 2011-02-18
"ffmpeg -i video.mkv -an -t 100 -vcodec libxvid -vtag XVID videoonly.avi"

created a video file that wasn't viewable by my PS3.  :(

But, using the DivX/MPEG-4 option in deVede did work!  Thanks everyone!

Greg

---

