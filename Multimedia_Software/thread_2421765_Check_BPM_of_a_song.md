---
title: "Check BPM of a song"
date: 2019-06-26
forum: Multimedia Software
---

### Post by joshuax12 on 2019-06-26
Hello,
I want a software or just a simple tool that can help me to detect the BPM of a song..
Thanks !

---

### Post by Frogs Hair on 2019-06-26
There is a possible solution at the link if the song is on mp3. There is a Chrome extension on the bottom of the page as well. The other alternatives I found are Windows only software. 

 [https://getsongbpm.com/tools/audio](https://getsongbpm.com/tools/audio)

---

### Post by again? on 2019-06-26
Install a metronome and click to the beat.
```
sudo apt install gtick
```
[ATTACH=CONFIG]283508[/ATTACH]

There is also bpm-tools.
With bpm-tools installed you can use bpm-tag. (may need to install libsox-fmt-all for mp3)
eg
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] bpm-tag -f -n "/home/glen/Music/My_Music/J.J. Cale - After Midnight.mp3"**
/home/glen/Music/My_Music/J.J. Cale - After Midnight.mp3: 128.740 BPM
```
Don't know how accurate bpm-tag is though.
Using Frogs Hair link it shows 96bpm for this song which is about the same if I tap along with gtick.

---

