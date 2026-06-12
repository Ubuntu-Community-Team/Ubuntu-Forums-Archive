---
title: "Two advanced questions regarding VLC"
date: 2008-05-12
forum: Multimedia Software
---

### Post by airflow on 2008-05-12
Hi,

I'm having two different issues I have with VLC which I couldn't solve so far on my own. Perhaps anyone can help me here.

1) I changed my xorg.conf recently to a Xinerama-setup, which has the advantage for me that I can move windows from one display to the other. This works fine, but on the other hand now I can't play movies in VLC on the secondary screen in fullscreen. When I move the VLC-window on the secondary screen and switch to fullscreen, it still opens fullscreen on the primary screen. I looked in the settings (even advanced), but couldn't make it work. It works fine with Gnome Movie Player though, so perhaps there is a way...

2) With the second problem I struggle since I switched to Ubuntu. Sometimes I want to display movies which are encoded sub-optimal. What I mean is that if the movie is 16:9, but encoded in 4:3 with black strips on top and bottom. I have a display which has 16:9 format, and when I watch such a movie there fullscreen, I have a black strips on every side of the movie. This is not a surprise, it's logical - but still, is there a way to "zoom in" in to the movie in such cases to display the movie itself fullscreen? I didn't find a way in VLC. If it's not possible in VLC, can you name any other application which is capable of that?

Thanks a lot,
airflow

---

### Post by chewearn on 2008-05-12
> **airflow said:**
> Hi,

I'm having two different issues I have with VLC which I couldn't solve so far on my own. Perhaps anyone can help me here.

1) I changed my xorg.conf recently to a Xinerama-setup, which has the advantage for me that I can move windows from one display to the other. This works fine, but on the other hand now I can't play movies in VLC on the secondary screen in fullscreen. When I move the VLC-window on the secondary screen and switch to fullscreen, it still opens fullscreen on the primary screen. I looked in the settings (even advanced), but couldn't make it work. It works fine with Gnome Movie Player though, so perhaps there is a way...

Go to VLC preferences dialog, tick the Advanced options checkbox in the lower right corner; then find this category in the left pane:
Video > Output modules > XVideo > Screen for fullscreen mode
Change the value from 0 to 1.

If this doesn't work, choose another output modules e.g. X11; repeat changing the value.  You should be using one of the output module (the default is usually XVideo).


> 2) With the second problem I struggle since I switched to Ubuntu. Sometimes I want to display movies which are encoded sub-optimal. What I mean is that if the movie is 16:9, but encoded in 4:3 with black strips on top and bottom. I have a display which has 16:9 format, and when I watch such a movie there fullscreen, I have a black strips on every side of the movie. This is not a surprise, it's logical - but still, is there a way to "zoom in" in to the movie in such cases to display the movie itself fullscreen? I didn't find a way in VLC. If it's not possible in VLC, can you name any other application which is capable of that?

Thanks a lot,
airflow

Press "a" key to manually switch the aspect ratio while playback.  Press "c" to crop the black bars.  With some trial and errors, you should find what you are looking for.

---

