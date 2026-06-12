---
title: "New Tuner driver"
date: 2014-04-18
forum: Mythbuntu
---

### Post by water0101 on 2014-04-18
I have been using a PCTV Nanostick 290e to get Freeview HD in the UK (works well), so I thought I would get another one. Ordered off Amazon and turns out they have tweaked it into a Triplestick 292e for which there are no drivers and ceased production of the 290e!!

I was doing a search and found this guys blog [http://blog.palosaari.fi/2014/04/naked-hardware-15-pctv-triplestick-292e.html](http://blog.palosaari.fi/2014/04/naked-hardware-15-pctv-triplestick-292e.html) and he has built the drivers and there are on the GitHub and will be in the Linux Kernal build 3.16.

My question is how soon will this get into MythUbuntu and if it is not soon how do I get the driver into my MythUbuntu setup?

---

### Post by blm-ubunet on 2014-04-19
You might want to watch justinh's attempts here:
[http://irc.mythtv.org/ircLog/channel/1/history](http://irc.mythtv.org/ircLog/channel/1/history)
Or jump onto IRC freenode #mythtv-users.

The 292 device has different h/w & you are also trying to get it to work with dvb-t2.

You can build the latest v4l-dvb:
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)
The basic approach is not too onerous.
There are lots of dependencies..mostly build tools & header files.

A better mouse trap:
[http://www.linuxtv.org/wiki/index.php/W_scan](http://www.linuxtv.org/wiki/index.php/W_scan)

---

### Post by blm-ubunet on 2014-04-26
progress..
[https://tvheadend.org/boards/5/topics/10864?page=3](https://tvheadend.org/boards/5/topics/10864?page=3)

---

