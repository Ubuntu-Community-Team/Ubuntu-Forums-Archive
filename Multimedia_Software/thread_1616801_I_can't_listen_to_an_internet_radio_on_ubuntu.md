---
title: "I can't listen to an internet radio on ubuntu"
date: 2010-11-08
forum: Multimedia Software
---

### Post by keningar on 2010-11-08
Dear community, I am using the version 10.04 LTS of Ubuntu. I want to listen to an internet radio station, which I can listen without a problem in Windows. However, in Ubuntu nothing happens when I click the link. The URL of the radio station is [http://www.metro951.com/index.php](http://www.metro951.com/index.php). The link which starts the streaming has the words "RADIO EN VIVO".

Thank you all.

Keningar

---

### Post by ron999 on 2010-11-08
Hi
That radio station plays OK for me with Firefox browser and a plug-in.
The name of the plug-in is '**gecko-mediaplayer**', look for it in Synaptic Package Manager.

It's also possible to play the station using a stand-alone media player such as VLC or mplayer.

Like this:-
```
vlc http://streaming.metro951.com/metro
```
And this:-
```
mplayer http://streaming.metro951.com/metro
```

---

