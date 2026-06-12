---
title: "Extract image from video?"
date: 2013-02-26
forum: Multimedia Software
---

### Post by carl4926 on 2013-02-26
What would be a good way to pull good quality images from a video?

---

### Post by shantiq on 2013-02-26
**vlc**

then tools/preferences/hotkeys/set a hotkey for Take Video Snapshot

then  tools/preferences/video   and set directory for snapshots


then use hotkey while viewing   [i use F2]   if you have a wireless keyboard you can do this comfortably while viewing video; and not even need to stop


============================


and/or



**MPlayer** comes with a very nice and easy to use video filter that allows taking single or multiple screenshots. The syntax is simple:  [all formats]

```
mplayer -vf screenshot my_file.mp4
```


Simply pressing the 's' key takes a single screenshot in png format in the working directory. 

but shift+S  will take all frames/pictures until you hit ctrl+C


========================
[B]
XBMC[/B]


set folder    settings/system/Debugging/screenshot folder

then hit \   to get fullscreen

and use  PrtScn    to get single shots

---

### Post by carl4926 on 2013-02-26
Thanks

I had used full screen playback in smplayer > space to pause where I want the capture > then PrtSc

I'll try those other options to see if the quality differs

---

### Post by shantiq on 2013-02-26
all of these take a picture as is


so if 640x480 it takes that   ;   if 1920x1080 that   and so on

the quality of pic has to do with the definition of the vid

so they are all the same

the mplayer trick "shift+S" is good if you want every frame ; you can even time it and then plough through the lot    anyway   as you say av a try:KS

---

### Post by sudodus on 2013-02-26
Thanks for sharing :KS

---

### Post by carl4926 on 2013-02-26
Great tips, thanks !

---

### Post by andrew.46 on 2013-03-09
The MPlayer command can be extended for those who like playing with such things, have a look at this wiki page:

[https://help.ubuntu.com/community/MPlayerTips#Tip_5:_Taking_screenshots](https://help.ubuntu.com/community/MPlayerTips#Tip_5:_Taking_screenshots)

---

### Post by shantiq on 2013-03-09
thanx Andrew could never find that detailed explanation of yours...   only remembered the basics for mplayer::]

---

### Post by andrew.46 on 2013-03-09
> **shantiq said:**
> thanx Andrew could never find that detailed explanation of yours...   only remembered the basics for mplayer::]

No problems, it is a pity that the wiki page has been forgotten... I put a huge amount of work into that one :(.

---

