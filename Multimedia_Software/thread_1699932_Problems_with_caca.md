---
title: "Problems with caca"
date: 2011-03-04
forum: Multimedia Software
---

### Post by radon7 on 2011-03-04
I am having problems with caca(text based rendering). If I run vlc or mplayer from a terminal window in gnome, it works great. If I switch to the terminal at F1(Ctrl+Alt+F1), the output starts flickering and only part of(mostly the top) the picture appears. I am running the following command.

mplayer -vo caca ./video.mpg

I also tried
CACA_DRIVER=ncurses mplayer -vo caca ./video.mpg

I would like to know how to fix the output and where I can find more info. All google gives me is the above command and mplayers documentation(which gives nothing for caca). aa has a little more documentation but not much.

---

