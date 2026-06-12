---
title: "No more video, just terminal screens."
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by Cherub_Rocky on 2007-11-05
I'm running gutsy (kubuntu) on an AMD 64 4600+ and a Nvidia 7900GT, I bought a new monitor today, (Soyo Topaz S 24") and changed the hardware settings to Generic 1920x1600 and changed the reslution accordingly, it the requested I restart the xserver, so I did. Now all I get is the terminal screen for a login in screen and I am clueless how to get my graphics back. Please HELP!!!!

---

### Post by K.Mandla on 2007-11-06
Something went awry with your video setup. Start your machine to that terminal login, then try 

```
sudo dpkg-reconfigure xserver-xorg
```
Follow the prompts; you'll probably have to restart your machine for the changes to take effect.

If that doesn't work you might have to try editing the xorg.conf file by hand, to get the settings correct.

---

