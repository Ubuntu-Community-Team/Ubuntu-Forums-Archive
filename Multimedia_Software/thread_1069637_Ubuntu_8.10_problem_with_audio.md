---
title: "Ubuntu 8.10 problem with audio"
date: 2009-02-14
forum: Multimedia Software
---

### Post by sukumar108 on 2009-02-14
I have installed Ubuntu 8.10 after formating my old WinXP. With little difficulty I could able to install it. There is a sound during login page but when I try to play some mp3 music using the Rhythmbox, it doesnot moves i.e. the paly time is 0.0 only. Then after I searched these forums and tried few things. As suggested some where I have installed VLC also. In VLC the Video is playing without audio.

Pls help... 

Note: I am new to linux.

Thanks in advance... ;-)

---

### Post by sukumar108 on 2009-02-14
I have installed Ubuntu 8.10 after formating my old WinXP. With little difficulty I could able to install it. There is a sound during login page but when I try to play some mp3 music using the Rhythmbox, it doesnot moves i.e. the paly time is 0.0 only. Then after I searched these forums and tried few things. As suggested some where I have installed VLC also. In VLC the Video is playing without audio.

Pls help... 

Note: I am new to linux.

Thanks in advance... ;-)

---

### Post by golusweet on 2009-02-14
open Terminal from Apps > Accessories > Terminal

Type : sudo apt-get install ubuntu-restricted-extras.

:)

---

### Post by x33a on 2009-02-14
you'll have to install extra plugins, since ubuntu doesn't come with default mp3 support.

copy and paste this in a terminal
```
sudo aptitude install gstreamer0.10 FAAD gstreamer0.10-plugins-ffmpeg gstreamer0.10-plugins-bad-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0
```

---

### Post by bapoumba on 2009-02-14
Threads merged.

---

