---
title: "Flash 10 in Firefox has a weird sound issue"
date: 2009-06-09
forum: Multimedia Software
---

### Post by Zaff on 2009-06-09
Hi there,
I have two computers, one runs Jaunty (upgraded from Intrepid when it came out) and the other runs Hardy.

Now Jaunty has flash 10 by default, and I manually installed flash 10 on my Hardy machine because of some flash game I wanted to try.

I have noticed though, ever since I've been using flash 10 on both machines, that after a while of leaving firefox running, if I play a video or a sound using flash, the sound will be hacked (that makes any sense ?). Basically it cuts for half a sec, goes back a bit and plays, cuts again, and so on. I have to restart firefox for it to work properly.
 It seems to be doing this after firefox has been launched for a while. Now this isn't a big deal but it is annoying and I'd like to know if anyone's been having the same problem and if there is a fix.

Cheers guys.

---

### Post by carlspam1 on 2009-06-10
> **Zaff said:**
> Hi there,
I have two computers, one runs Jaunty (upgraded from Intrepid when it came out) and the other runs Hardy.

Now Jaunty has flash 10 by default, and I manually installed flash 10 on my Hardy machine because of some flash game I wanted to try.

I have noticed though, ever since I've been using flash 10 on both machines, that after a while of leaving firefox running, if I play a video or a sound using flash, the sound will be hacked (that makes any sense ?). Basically it cuts for half a sec, goes back a bit and plays, cuts again, and so on. I have to restart firefox for it to work properly.
 It seems to be doing this after firefox has been launched for a while. Now this isn't a big deal but it is annoying and I'd like to know if anyone's been having the same problem and if there is a fix.

Cheers guys.



Me too.

2009-06-10
Toshibe Equium Laptop
Firefox 3.0.10
Linux ****_laptop 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686 GNU/Linux
Ubuntu 9.04 \n \l
Flash 10.00.22.87
Sound is know to work with hydrogen, VLC, Ardour etc so I know my system is fairly compus mentus.
The Ubuntu 9.04 was not a clean install, it was an upgrade from 8.04 via 8.10

anyway, heres the issue:

Flash video starts, eg youtube. Works OK for a while (10-15 minutes).
Then sound goes very very choppy for several seconds and eventually dies altogether.
The only solution appears to be a firefox restart.
Hard to explain sound glitches, but imagine a stereo sampled singer going laaaaaa once every second.
The sound goes from
laaaaaaa laaaaaaa laaaaaa laaaaaa laaaaaa laaaaaa laaaaaa
to
laaaa b   d d  d b  b bd   bd bd b  d  b    d  b    dd   b   d   (silence)
where the "buh" and "duh" randomly go from extreme left to right. its wierd.

Also if firefox/youtube is left up for a while (hours), when I come back and play the video its very choppy, even when i reload the page. Again, the only option is to restart firefox.

Hope that helps someone to debug. Its certainly out of my skill set.

---

### Post by Zaff on 2009-06-10
You've described the sound issue better than I would have :)
This is exactly what's going on with me too.

---

### Post by graza99 on 2009-06-10
I'm also getting this issue running Adobe Flash 10 player in Firefox 3.0.10 on Kubuntu 8.10. It only seems to happen intermittently and a Firefox restart doesn't always seem to fix it.

---

