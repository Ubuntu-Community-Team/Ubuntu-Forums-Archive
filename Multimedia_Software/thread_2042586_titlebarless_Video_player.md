---
title: "titlebarless Video player"
date: 2012-08-14
forum: Multimedia Software
---

### Post by bonzaicounterpunch on 2012-08-14
Is there a video player that is able to play video without a title bar?  

[[IMG]http://s11.postimage.org/ggcbh21y7/11111111.jpg[/IMG]]("http://postimage.org/image/ggcbh21y7/")

---

### Post by johnathansmith on 2012-08-14
Hi, use VLC player and look [here]("http://superuser.com/questions/201667/how-to-disable-all-window-borders-from-the-vlc-playback-window")
```
"View" menu > "Minimal View".

That hides all the buttons and menus, but leaves the window border and windows minimize/maximize/close buttons.


```

---

### Post by ads52 on 2012-08-16
You can do this with the MPlayer commandline:

```
mplayer -noborder my_file
```

where of course 'my_file' will need to be the name of *your* movie file.

---

