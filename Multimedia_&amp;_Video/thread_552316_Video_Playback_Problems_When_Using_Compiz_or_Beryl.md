---
title: "Video Playback Problems When Using Compiz or Beryl"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by ashwinhgtx on 2007-09-16
I just shifted to ubuntu some weeks back. I can't play videos when i've enabled compiz or beryl. i haven't tried compiz fusion yet. I only get the sound no video. Without the desktop effects it's fine. I have Fiesty running on a Thinkpad R60 with onboard graphics solution-i think it's by intel with 128MB shared video memory. when i double click to make it fullscreen i can see the video for a sec.ie.during the transition then it's all black again in the full screen mode. when returning back to normal size i get the same effect. i've tried VLC, totem and mplayer. Please help.:(

---

### Post by raul_ on 2007-09-16
You have to use the "xshm" driver (or something like that, i don't really remember the name". Try to browse through your player's menus until you find the "video driver" option

---

### Post by Seamyst on 2007-09-16
I had the same problem... [this thread]("http://ubuntuforums.org/showthread.php?t=531140&highlight=avi&page=2"), post 18, did it for me.

---

### Post by ashwinhgtx on 2007-09-17
Thanks dude. changing the default video output to x window system(no Xv) and then doing the same in VLC did the job for me. Time for some movies now!!:popcorn: 
and to impress my friends...:KS

---

