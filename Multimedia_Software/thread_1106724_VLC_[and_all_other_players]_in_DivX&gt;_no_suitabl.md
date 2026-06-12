---
title: "VLC [and all other players] in DivX:&gt; no suitable decoder module for fourcc `DXSB'"
date: 2009-03-26
forum: Multimedia Software
---

### Post by Vahids on 2009-03-26
i try to play DivX movies (.divx) but, when i try to set subtitle of the movie in **mpayer** when right click >> Video >> Track >> track 2 ::> i have this [COLOR="Red"]**Error**[/COLOR]:
```

Cannot find codec matching selected -vo and video format 0x42535844.

```
and in **VLC** i have this [COLOR="Red"]**Error**[/COLOR]:
```

main decoder error: no suitable decoder module for fourcc `DXSB'.
VLC probably does not support this sound or video format.

```
in **smplayer** when i set track 2 of video just play audio without video :(

*** My .divx movies had a hard subtitle in .dix file ! noting srt OR idx or any subtitle file exist,
just a .divx file, this file can had more than 1 subtitle whit herself!!!

---

### Post by Vahids on 2009-03-26
Bing !!!!!! noting ?!!!!!!!!! ANSWER !!!!!
Come on, help me! Please. it's just my problem in linux! i didn't have like this problem in WINDOW$ please help me!:popcorn:

---

### Post by rvm4000 on 2009-03-26
It seems currently there's no support for dxsb subtitles in the linux players (at least mplayer & vlc).

---

### Post by Vahids on 2009-03-26
> **rvm4000 said:**
> It seems currently there's no support for dxsb subtitles in the linux players (at least mplayer & vlc).
No any way ?!!! :(

---

### Post by rvm4000 on 2009-03-26
It seems dxsb is a proprietary format. Maybe it's not easy to add support for it.

All I have found (for vlc) is this:
[http://forum.videolan.org/viewtopic.php?f=12&t=12391](http://forum.videolan.org/viewtopic.php?f=12&t=12391)
[http://forum.videolan.org/viewtopic.php?f=12&t=34981](http://forum.videolan.org/viewtopic.php?f=12&t=34981)
[http://trac.videolan.org/vlc/ticket/2383](http://trac.videolan.org/vlc/ticket/2383)

In the mplayer mailing lists I have found nothing about it.

Maybe you can suggest to add support for it in [mplayer-users list](https://lists.mplayerhq.hu/mailman/listinfo/mplayer-users).

---

