---
title: "Gutsy - no video codecs"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by Oldbugger on 2007-10-25
Fresh install of 7.10 and am unable to install any video codecs. When I ask it to find them it finds Mplayer but when I ask it to install it says it needs another file but just says it "will not be installed". So at the moment I have no video????

Actually it appears I cannot install any software with proprietary stuff in it....I just tried to install Opera and got the same message?????

---

### Post by Qwerty_ on 2007-10-25
You will mostly likely need check that you have all sources selected.

System>Administration>Software Sources.

---

### Post by jenhsun on 2007-10-25
> **Oldbugger said:**
> Fresh install of 7.10 and am unable to install any video codecs. When I ask it to find them it finds Mplayer but when I ask it to install it says it needs another file but just says it "will not be installed". So at the moment I have no video????

Actually it appears I cannot install any software with proprietary stuff in it....I just tried to install Opera and got the same message?????

In your software sources, enable main, restricted, universe and multiverse.
( I just enable everything...)
Then Go to add/remove and find "gstreamer", remember to SHOW ALL AVAILABLE APPLICATION
download them all then you will have your codec.

---

### Post by pierrot on 2007-10-25
I do everything u say,but still can`t play any movie :confused:
i try and Mplayer, and Totem Xine...nothing. I would be pleased if u can help me...

I see only moving color lines,don`t know the english word to explane better....

---

### Post by Oldbugger on 2007-10-25
I have enabled all sources and still no-go. It just will not select or when it does it says it will not install the files???????

---

### Post by jenhsun on 2007-10-26
Here are some possible solutions:
1. Make sure your sound card is working.
2. Since the codec involve country restricted, could you change your system's country location? And tell us your result.
3. Please test the other video or music files that without the need of codec, see what's going on. We need to narrow down the problems.

---

### Post by Oldbugger on 2007-10-26
I used sudo apt-get install in a terminal and it installed fine....as did Opera and K3b....

As I mentioned in the other post in the General area...it seemed to be any restricted software. It appears that the GUI bit of Gnome didn't seem to recognise that even logged in as root (which I enabled) to install proprietary stuff. 

All well now using the terminal...not very noob friendly though....

---

