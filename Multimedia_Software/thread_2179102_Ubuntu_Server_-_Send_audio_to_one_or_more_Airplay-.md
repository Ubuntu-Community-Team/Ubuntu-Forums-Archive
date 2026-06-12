---
title: "Ubuntu Server - Send audio to one or more Airplay-devices"
date: 2013-10-06
forum: Multimedia Software
---

### Post by Daniel_Jansson on 2013-10-06
I have ceiling speakers in 6 rooms controlled by 6 Apple Airport Express and Airplay. This works excellent.
I also have a home automation system from Fibaro based on the z-wave technology. ([http://www.fibaro.com](http://www.fibaro.com))

What I would like to to is to be able to start and stop music (online radio or a local file) in one or more rooms.
The home automation system does not have support for this. But it has support for LUA scripts.

So my thoughts are to purchase a Raspberry Pi and install Ubuntu Server on it. (that is the easy part)
But my question is this:

[B]Is there any available software to start/stop online radio streams or local files on one or more airplay-devices
for an Ubuntu Server installation?

[/B]If there is, I think it would be rather easy to create a php-script that can be invoked from the home automation system.
(For example a*irplayProxy.php?action=play&file=[http://http-live.sr.se/p3-mp3-192](http://http-live.sr.se/p3-mp3-192)&zones=1,2,3* and *airplayProxy.php?action=stop&zones=1*)

Any ideas about this?

---

