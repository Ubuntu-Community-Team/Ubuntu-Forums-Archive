---
title: "DVD's playing sideways gxine errors and codec issues"
date: 2008-07-02
forum: Multimedia Software
---

### Post by e1ektrob0y on 2008-07-02
I have had major issues getting DVD's to play correctly on my system. I followed the guides and installed medibuntu w32codecs css2 dvdread regionset, you name it i installed it. Anyway, as we all know MoviePlayer has no menu feature for DVD's so thats no good to me. VLC plays the DVD's sideways like on a 90 degree rotation. Also, VLC and Mplayer the colours are all messed up like green is orange and red is green. Gxine just gives the error ```
The xine engine failed to start.
No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

```
and 
```
read error from /dev/dvd
``` I read somewhere that this can happen if you have two dvd drives so i took one out...still the problem is the same :( can anyone help me PLEEEEASE! I just want to watch a dvd so bad :(

---

### Post by markbuntu on 2008-07-02
VLC will rotate the images if you tell it to, same with mplayer. You can try fooling around with the filters to get the colors correct. You should really explore the preferences menus of these programs. But be prepared for crashes if you fool around with the output video mode.

You need the xine plugins to get Gxine to work.

---

