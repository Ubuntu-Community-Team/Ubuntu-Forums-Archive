---
title: "Can't get werbradio to work either on FF or Opera."
date: 2008-04-25
forum: Multimedia Software
---

### Post by bstrd on 2008-04-25
Hi,

I'm not very good at this linux- thing, so i was wondering if someone could help me.

I'm often listening to webradio (streaming), but in Ubuntu, i cant get it to work.
I think it is because the streaming needs wmplayer plugin to work.
Is there any way to work around this?

The webradio i'm listening to is: [http://www.radioseven](http://www.radioseven)[dot]se

Ubuntu 8.04
Firefox 3.0 beta 5

Thank you.:)

---

### Post by rotten777 on 2008-04-25
Seems like a common problem.

```
sudo apt-get install alsa-oss
```

Then go to System-> Preferences-> Sound-> Devices Tab-> Choose ALSA

---

### Post by bstrd on 2008-04-26
That did'nt do it. I still need the windows media player plugin!

Is there any way to listen to webradio without having to install the wmplayer plugin?:confused:

---

### Post by olofcadiz on 2008-05-13
Hi

I could hear webradio with ubuntu 7.10
After I have upgraded to 8.04 I have lost the possibility to listen to news from [http://www.sr.se/ekot/](http://www.sr.se/ekot/)
Still I can hear some music channels

Anyone who have solved this problem in ubuntu 8.04?

Ubuntu 8.04
Firefox 3 Beta 5
Epiphany
ALSA

---

### Post by gandaran on 2008-05-13
if the totem-plugin can't deliver, you can try others, mplayer-plugin, vlc-plugin or xine-plugin! try them until you find the best one that works on that site.

(mplayer needs w32codecs from the medibuntu repository)

I tried [http://www.radioseven.se/](http://www.radioseven.se/) (don't know if it's the same site you mentioned) and the windows media works fine in totem (gstreamer) plugin on firefox, opera doesn't work with the totem plugin!
check in synaptic if all the gstreamer plugins are installed.

---

### Post by olofcadiz on 2008-05-16
I can listen on [http://www.radioseven.se](http://www.radioseven.se) 
My problem is when I connect to
[http://www.sr.se/webbradio/webbradio.asp?type=latestbroadcast&Id=83&BroadcastDate=&IsBlock=0](http://www.sr.se/webbradio/webbradio.asp?type=latestbroadcast&Id=83&BroadcastDate=&IsBlock=0)
I cannot listen to "Ekot" but I can listen to music on the lower left on the site above.
I have tried Firefox, Epiphany and Opera with the same bad result.:confused:

---

### Post by olofcadiz on 2008-05-16
Many thanks Gandaran.
After trying again I can use Opera to listen.
Still not Firefox and Epiphany.:)

---

