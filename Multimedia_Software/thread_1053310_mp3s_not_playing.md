---
title: "mp3s not playing"
date: 2009-01-28
forum: Multimedia Software
---

### Post by legatek on 2009-01-28
Very strange problem here. I am unable to play mp3s on my Hardy system. I don't have a problem with sound since I can play youtube videos with sound just fine, but when I launch an mp3 (which opens Totem by default) it loads the mp3, tells me that it's playing, and it sits at 0:00. If I seek forward by dragging the progress bar it forwards to that time, continues to tell me it's playing, and just sits there. No progress, no noises. If I open the mp3 in Mplayer it crashes the player.

I don't even know how to search the forums for the answer to this problem! Help!

---

### Post by neu2buntu on 2009-01-28
you may not have the codecs installed for mp3 playback. open the terminal and type
```
sudo apt-get install ubuntu-restricted-extras
```  you will have to have the restricted repositorys enabled also(if not already) by going to >system >administration >software sources and in the ubuntu software tab tick all boxes....  source code and cdrom are optional here

---

### Post by browndog on 2009-01-28
> **legatek said:**
> Very strange problem here. I am unable to play mp3s on my Hardy system. I don't have a problem with sound since I can play youtube videos with sound just fine, but when I launch an mp3 (which opens Totem by default) it loads the mp3, tells me that it's playing, and it sits at 0:00. If I seek forward by dragging the progress bar it forwards to that time, continues to tell me it's playing, and just sits there. No progress, no noises. If I open the mp3 in Mplayer it crashes the player.

I don't even know how to search the forums for the answer to this problem! Help!

Check out the sticky in this forum on getting multimedia to work...it provides command lines for a script that will download just about everything you need.  Then, set MP3's to open in Rythmbox, not Totem.  If you don't like Rythmbox you can try Banshee.

---

### Post by legatek on 2009-01-29
I already have everything I need. In fact, I was playing mp3s just a few days ago, but now it no longer works. As far as I recall, I only received updates for Vim in that time, so I have no idea what could have become broken.

---

### Post by legatek on 2009-01-29
Update: It was a glitch in the matrix. I just tried playing an mp3 and everything works just fine. No reboot, just let the system sit overnight and the problem worked itself out. Strange. Thanks for the replies, though.

---

