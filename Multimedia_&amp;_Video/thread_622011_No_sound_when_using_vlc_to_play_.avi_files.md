---
title: "No sound when using vlc to play .avi files"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by theseeker on 2007-11-24
Hi, 

well, I've this annoying one: VLC doesn't play sound in avi files on my laptop (asus f3sv), although Totem plays it normally. I changed the audio output module to ALSA, but nothing changed. Any ideas?

thanx :)

---

### Post by theseeker on 2007-11-25
Nobody? :confused: There must be something!

---

### Post by theseeker on 2007-11-26
bump

Please, help! There is no evident reason for what's happening. Totem handles sound ok but there are breaks in the movie motion. So there isn't a problem with alsa server or something. I could really use a helpful comment here! Thank you

---

### Post by theseeker on 2007-11-27
Solved:

```
sudo apt-get install vlc-plugin-*
```

:)

---

### Post by TWO on 2007-12-26
> **theseeker said:**
> Solved:

```
sudo apt-get install vlc-plugin-*
```

:)

Where did you find that command and what does it install that's missing from the original VLC repository?

Having tried the command I am still unable to get VLC to play some avi. files. I sometimes record film with my camera and VLC will play the video but no audio whatsoever...

---

### Post by Biznarie on 2008-01-07
> **TWO said:**
> Where did you find that command and what does it install that's missing from the original VLC repository?

Having tried the command I am still unable to get VLC to play some avi. files. I sometimes record film with my camera and VLC will play the video but no audio whatsoever...

I also have this problem, and I'm still having trouble playing some of avi's too.

---

### Post by dezine on 2008-01-21
That worked for me, thanks a million.

---

### Post by fliptomato on 2008-06-14
Hello -- sorry, just bumping this up. I tried sudo apt-get vlc-plugin-* , but I'm still not getting any audio on this avi file.

Any thoughts?

---

### Post by konungursvia on 2008-06-14
Another issue: many ripped dvds provide 5.1 dolby sound, and vlc often defaults to something else. You can therefore try going into Audio > and select stereo instead of 5.1.

---

