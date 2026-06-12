---
title: "mms port: listening or opening?"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by God Of Atheism on 2007-05-27
I'm trying to play:
mms://rntlivewm.rai.it/giro2007live#cf
The above does not broadcast at the moment (should only start in one to two hours), so instead I tried the one below:
mms://rntlivewm.rai.it/_rn24_live_
The latter is embedded in
[http://www.media.rai.it/mpmedia/0,,Livetv%5E21542,00.html](http://www.media.rai.it/mpmedia/0,,Livetv%5E21542,00.html)
I notice (in either case) that it tries to connect to port 1755, though it will after a while try port 80 instead. I do intend to open up port 1755 in iptables, but should I open it all together or should I open it as a listening port? Or should I instead forward the port to another port?

In addition, what settings should I use for mplayer to get a decent signal, I noticed yesterday with the first one that quite often it would start to stutter after a while, how could I prevent that from happening? The cache in use would just slowly but certainly drop down to 0 and the stuttering begin, I started mplayer from the terminal in order to see the messages, most of which I don't understand.

---

