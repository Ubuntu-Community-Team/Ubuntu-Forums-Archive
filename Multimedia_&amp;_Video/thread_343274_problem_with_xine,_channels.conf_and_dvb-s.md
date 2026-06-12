---
title: "problem with xine, channels.conf and dvb-s"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by HorstJENS on 2007-01-21
I have a problem watching satellite tv with  xine.

After a ubuntu edgy install, my dvb-s card (wintv nexus-s) get recognized by xine. I just have to copy the default channels.conf list from:

```
usr/share/doc/dvb-utils/examples/channels.conf-dvbs-astra nach
```
to 
```
~/.xine/channels.conf
```

and i can see tv with xine. The problem starts later. Because i have an hotbird satellite (Europe-South) just a few channels of this channels.conf for the astra satellite work. 
The first entry in channels.conf is "Das Erste..ARD" and let me watch the german tv ARD.
As soon as i switch to a channel that does not exist xine freeze and i have to restart xine.
After that, xine seem to be unable to find any channels. It says an error message:
**"no plugin to handle dvb:das Erste**" 
no matter what i do. Even removing all of .xine, deinstalling xine, reinstalling xine, creating a new channels.conf ... all does not help.

So where does xine save the information about dvb-s channels if not in ~/.xine ?

---

### Post by DerHesse on 2007-01-21
[http://www.zwez.com/sat/vdr/vdr_1.3.x/index.html](http://www.zwez.com/sat/vdr/vdr_1.3.x/index.html) has a channels.conf for hotbird.

and as I see you are from australia :-\", have a look here:
[http://www.vdr-wiki.de/wiki/index.php/Channels.conf](http://www.vdr-wiki.de/wiki/index.php/Channels.conf)
[http://www.vdr-wiki.de/wiki/index.php/Dvb-apps_dvbscan](http://www.vdr-wiki.de/wiki/index.php/Dvb-apps_dvbscan)
or [http://vdr-portal.de](http://vdr-portal.de)
[http://forum.ubuntuusers.de/topic/41818/?highlight=xine+channels+conf](http://forum.ubuntuusers.de/topic/41818/?highlight=xine+channels+conf)

to find your channels.conf try

> $ find / -name channels.conf 2> /dev/null

---

### Post by HorstJENS on 2007-01-21
Thanks for the links. The problem is solved now. (a still running xine process was giving me a headache).
I'm from Austria, not Australia :-)

---

### Post by DerHesse on 2007-01-21
Ach, ok, the better. Otherwise you would have problems following the links I provided.
:lolflag:

---

