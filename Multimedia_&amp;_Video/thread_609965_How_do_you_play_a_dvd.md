---
title: "How do you play a dvd"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by System Monitor on 2007-11-11
Whenever i try to play a dvd it doesnt work, i think i need some plugin. i am not sure how to get. It is a commercial dvd by the way, so it is encrypted.

---

### Post by onestep on 2007-11-11
To watch encrypted DVDs I use use totem-xine insted of totem-gstreamer.

Applications/Accessories/Terminal

then copy & paste the following 

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

