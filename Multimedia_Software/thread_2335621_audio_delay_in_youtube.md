---
title: "audio delay in youtube"
date: 2016-08-30
forum: Multimedia Software
---

### Post by dimas869 on 2016-08-30
i am using Ubuntu 16.04 and when i play a youtube video and there is a delay in the audio or should i say the picture? as the audio ends and the video still play what it suppose to be what the audio few seconds before

thanks for your help

---

### Post by &amp;KyT$0P# on 2016-08-30
What browser?
Are you playing the video with Flash player or HTML5?

I've had sound lagging when using Flash 11.2 NPAPI, and that issue happens on **every .swf**, not just YouTube.

---

### Post by Portaro on 2016-09-01
Maybe you need change the resolution of video emition "quality" for example to 1080 p to 480 or else, in some videos specially in direct streamings I also have this problem ,  if your pc is old like mine maybe can be this change that you need .

---

### Post by shantiq on 2016-09-09
youtube not ideal through browsers and often check if machine not of the latest design

**SO** to avoid using all browsers gives better results
two ways to get smooth play are:


&#10112;   play through **kodi** youtube add-on
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi
```



&#10113;   play through **mpv**

```
sudo apt install mpv
```

then mpv + youtube url   ex:  ```
mpv https://www.youtube.com/watch?v=aAlWUne3S8w
```

or use **vlc **[copy url then ctrl+v] or **cvlc **or **nvlc** from command line

the easiest way    ```
cvlc https://www.youtube.com/watch?v=aAlWUne3S8w
```

---

### Post by Yellow Pasque on 2016-09-10
Is it just youtube/streaming or does it happen if you play a local video as well?

---

