---
title: "XawTv-Compiz conflict"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by diego1188 on 2007-11-18
Hello. I use XawTv with my old Hauppauge WinTvUsb tv-card (with Usbvision driver), as it seems the only tv-app that can make that card work. 
Recently I finally got Compiz running on the pc (I've got an Ati Radeon Xpress X200M graphic card, what a pain...), but I found out that XawTv and Compiz/Beryl are incompatible; when I launch XawTv I get a black screen and I must restart X. I also tried to switch to Metacity, but the result is the same. The only solution seems to restart X using a non-fglrx driver before launching XawTv.
Can anybody perhaps give me a suggestion about this conflict?
Thanks, diego

---

### Post by maitrebart on 2008-07-18
1. When you start xawtv, add the -noxv option.

2. After the screen gets black, switch to virtual console 1 (xtrl-alt-f1). Wait to see the console screen. Then switch back to X (ctrl-alt-f7). You should see the video.

You may have a look at this thread also:

[http://forum.compiz-fusion.org/archive/index.php/t-1152.html](http://forum.compiz-fusion.org/archive/index.php/t-1152.html)

---

