---
title: "dtvtuner help"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by NCAANFI on 2007-07-12
I installed Ubuntu on my HTPC, it's great very happy. I just need to fix one thing before I can call it a day. I want to setup my Leadtek DTV1000 card so I can use TvTime or MythTv. It's on the supported list. I know that the remote probably won't work but that's ok the bluetooth mouse is good enough. 

Now I've seen this
[http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29#Generic_Installation](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29#Generic_Installation)
and I really have no clue how to go about and get this done. I have no idea what compiling a kernel is. I just basically cut and pasted commands from the ubuntu forums to get it up and running. I'm not even sure if the card is working properly

Any help? A step by step guide would be appreciated.

---

### Post by r76 on 2007-07-13
It sounds like it works without any compiling required [here]("http://www.linux.com/feed/115561")

Start with something simple to test your TV card works before diving into MythTV or FreeVO etc.  I use Kaffeine, it can be installed from the repositories (get libxine-extracodecs while you're there), should recognise your card and go!  Or you could try using the dvb-utils package... if you know it works first, proceeding will be a lot easier.

---

### Post by Canarygsr on 2007-07-17
I just made the switch from fedora (and it worked out of the box) to the new fiesty and the DTV1000 doesnt seem to work for me either, Now it does show up in some sections of the tuner card setup in myth but not in the DTV section V3.X..... 
Any Ideas?

---

### Post by Revolution on 2007-07-25
I did a bit of research and wrote this post.

[http://ubuntuforums.org/showthread.php?p=3077444#post3077444](http://ubuntuforums.org/showthread.php?p=3077444#post3077444)

Hope it helps.

---

