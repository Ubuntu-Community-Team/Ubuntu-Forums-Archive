---
title: "Terminal music player"
date: 2012-01-26
forum: Multimedia Software
---

### Post by TheAJGman on 2012-01-26
I'm looking for a in line terminal music player. I need it so that I can make rolling lyrics. So it needs to be like:
```
play /home/TheAJGman/Music/Green_Day/Kerplunk/Christie_Road.mp3
```
and then it needs to run commands while playing the song.

---

### Post by papibe on 2012-01-26
Try mplayer. It is on the Sofware Center.

> and then it needs to run commands while playing the song.
What do you mean by that? Like shorcuts to forward and rewind?

Regards.

---

### Post by TheAJGman on 2012-01-26
> **papibe said:**
> Try mplayer. It is on the Sofware Center.


What do you mean by that? Like shorcuts to forward and rewind?

Regards.

No I mean it starts playing the song when the command is entered and thats it. nothing else. you can keep entering commands. I could never get Mplayer to work right
EDIT: got mplayer working. How do I have it play a song it the background without it hogging up the terminal.
EDIT2: got it ```
mplayer -really-quiet ~/music/Artist/Song.mp3 < /dev/null
```

---

### Post by andrew.46 on 2012-01-26
> **TheAJGman said:**
>  How do I have it play a song it the background without it hogging up the terminal.

Perhaps see if your terminal emulator supports multiple 'tabbed' windows? I believe most do....

---

