---
title: "video playback restarts gdm everytime"
date: 2011-05-20
forum: Multimedia Software
---

### Post by psycho5 on 2011-05-20
I recently upgraded from 10.04-11.04 using the 11.04 CD 

I don't use any effects, I log on the sessions using Ubuntu classic (no effects) . Whenever I try to play a video, the gdm restarts and puts me back at the login screen. I installed vlc thinking it might help but no deal. Can anyone help me solve this? Thanks a lot.

*edit*  I tried all different types of video outputs in vlc, the default seems to work the best, but as soon as I click the vlc window, try to resize it, or access any menu on vlc or try to fullscreen the video gdm crashes and restarts.

---

### Post by jerrrys on 2011-05-21
could it be [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=vlc+memory+leak&as_qdr=all&sa=Google+Search&lang=en#851](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=vlc+memory+leak&as_qdr=all&sa=Google+Search&lang=en#851)

---

### Post by psycho5 on 2011-05-22
Hi, thanks for ur reply. I think it was a unichrome driver problem. I downloaded and installed the driver from unichrome/trunk now the videos are playing fine.

---

### Post by soliddiesel on 2011-06-20
install vlc, and although that also crashes when trying to load any  video. All it took to fix it was to go into vlcs advanced video  properties and change the video output module to X11. fixed everything  right up for me.

---

