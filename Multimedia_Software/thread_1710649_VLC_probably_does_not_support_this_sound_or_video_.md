---
title: "VLC probably does not support this sound or video format"
date: 2011-03-20
forum: Multimedia Software
---

### Post by Kajoo on 2011-03-20
Hi. 
I just reinstalled yesterday Ubuntu on my second PC, I didn't use 2nd PC for a while so I decided it is time to refresh Ubuntu on it.

I installed sopcast to watch some football games. I setup VLC as a main player, so when I past address to sopcast and start bufforing VLC turned on and I was able to watch game, after sec some small windows with error appeared sayin' "VLC probably does not support this sound or video format "wmap"" I closed this windows and noticed there is no sound... I don't know how to fix this problem it never happend before.


ps. sorry for my english I still learning. Thanks.

---

### Post by Kajoo on 2011-03-20
The problem solved itself it's seems sound doesn't working on some channels especially the russian ones. There is no problem with others channels.

---

### Post by dyadyayura on 2011-04-09
use gnome-mplayer

---

### Post by andrew.46 on 2011-04-09
> **Kajoo said:**
>  "VLC probably does not support this sound or video format "wmap"

I suspect the problem is that your copy of vlc is compiled against an older copy of libavcodec that does not have the wmapro decoder. I attach a screenshot of vlc playing a wmapro file to show it *can* be done with a more recent copy. Goom is also being used which is rarely compiled in :(.

---

