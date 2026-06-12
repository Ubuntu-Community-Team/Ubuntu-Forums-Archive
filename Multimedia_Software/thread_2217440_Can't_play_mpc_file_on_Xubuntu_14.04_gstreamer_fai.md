---
title: "Can't play mpc file on Xubuntu 14.04 gstreamer failed"
date: 2014-04-17
forum: Multimedia Software
---

### Post by kosiek2 on 2014-04-17
Hi.
When I try to play mpc file on Xubuntu 14.04 i get this message error:
Playing error : Can't decode stream. at /usr/bin/../share/gmusicbrowser/gmusicbrowser_gstreamer-0.10.pm line 137.

---

### Post by mc4man on 2014-04-17
see my next post...

---

### Post by andrew.46 on 2014-04-17
And of course MPlayer (and SMPlayer) should have no problem with such files:

```

andrew@skamandros~$**[COLOR="#FF0000"] mplayer -ac help | grep -i musepack[/COLOR]**

ffmusepack7 ffmpeg    working   Musepack sv7 audio codec  [mpc7]
ffmusepack8 ffmpeg    working   Musepack sv8 audio codec  [mpc8]
musepack    mpcdec    working   Musepack audio codec

```

It is a great pity that mpc files never really took off as sound quality is pretty good to my untutored ears and the encoder trouble free.

---

### Post by mc4man on 2014-04-17
After a bit of a look - 
gmusicbrowser doesn't use the gstreamer ffmpeg plugin for mpc, it uses libmpcdec6 & possibly the gst bad plugin (not sure about the plugin.
I guess if you want to possibly track down then see when did it stop playing mpc, it does here in 12.04, not in 14.04, did it work thru 13.10??

Edit: the issue is with the version of libmpcdec6 in trusty, (libmpc (2:0.1~r459-1ubuntu3),  if I downgrade to the precise/saucy version (libmpc (2:0.1~r459-1ubuntu1),  then gmusicbrowser plays mpc
There is very little difference between the 2 versions, but at least in terms of gmb something is amiss, you likely can downgrade libmpcdec6 with no real issue - 
[https://launchpad.net/ubuntu/+source/libmpc/2:0.1~r459-1ubuntu1](https://launchpad.net/ubuntu/+source/libmpc/2:0.1~r459-1ubuntu1)

---

