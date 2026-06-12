---
title: "Help Please Amarok Can't Play MP3's?"
date: 2008-05-04
forum: Multimedia Software
---

### Post by cchester on 2008-05-04
Hey guys,

I have run into a problem with Amarok. It says it can't play mp3's. I have included a screen shot. I clicked on install mp3 support but nothing. Does it not play all mp3's?

Thanks for any help.

---

### Post by NightwishFan on 2008-05-04
```
sudo apt-get install libxine1-ffmpeg
```
Also make sure you are using xine engine.

---

### Post by cchester on 2008-05-05
> **NightwishFan said:**
> ```
sudo apt-get install libxine1-ffmpeg
```
Also make sure you are using xine engine.

Synaptic shows that it is already installed. By the way other mp3's that I have played through Amarok have played but I ran across that one that would not play and that message popped up when I tried it.

Thanks for anymore help.

---

### Post by NightwishFan on 2008-05-05
It should play mp3s, with xine engine and libxine1-ffmpeg. Remember to restart Amarok after you install the package. If you have done these, perhaps consider running this command with amarok closed:
```
sudo apt-get update && sudo apt-get purge amarok && sudo apt-get install amarok && echo "Installation Finished"
```

---

### Post by cchester on 2008-05-05
> **NightwishFan said:**
> It should play mp3s, with xine engine and libxine1-ffmpeg. Remember to restart Amarok after you install the package. If you have done these, perhaps consider running this command with amarok closed:
```
sudo apt-get update && sudo apt-get purge amarok && sudo apt-get install amarok && echo "Installation Finished"
```

Will try out what you said. Thanks.

---

### Post by thilina on 2011-02-10
If amarok refuses to play mp3/mp4/m4a/mpg's even after installing the necessary codecs, you better try this simple guide.

[http://blog.ishans.info/2011/02/10/cant-play-songs-in-amarok-after-installing-it-in-ubuntu/](http://blog.ishans.info/2011/02/10/cant-play-songs-in-amarok-after-installing-it-in-ubuntu/)

---

