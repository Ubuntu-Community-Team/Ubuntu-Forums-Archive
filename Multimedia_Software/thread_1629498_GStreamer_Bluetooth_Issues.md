---
title: "GStreamer Bluetooth Issues"
date: 2010-11-23
forum: Multimedia Software
---

### Post by Sergius14 on 2010-11-23
Hi, I could pair my Motorola S9-HD Headphones with my Ubuntu 10.10 succesfully.

At sound preferences sound test are working fine.

If I run gstreamer-preferences from bash, and the switch to ALSA, sound test also runs fine over the headphones.

Music / Video also runs fine (and very well) using VLC, but I can't make it work with Banshee / Totem / Rhythmbox.

It has to be related to GStreamer.

Banshee does a play/stop/play/stop a couple of time and then stops (or crashes).

This is the banshee log:

[Info  21:17:27.426] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 20
10-10-26 18:21:18 UTC]
[Info  21:17:29.168] Updating web proxy from GConf
[Info  21:17:29.282] All services are started 1,516436
[Info  21:17:30.662] nereid Client Started
[Error 21:20:22.738] GStreamer core error: StateChange
[Error 21:20:24.020] GStreamer core error: StateChange
[Error 21:20:25.292] GStreamer core error: StateChange
[Error 21:20:25.430] GStreamer core error: StateChange
[Error 21:20:26.915] GStreamer core error: StateChange

Unhandled Exception: System.NullReferenceException: Object reference not set to 
an instance of an object
at Banshee.GStreamer.PlayerEngine.OnAboutToFinish (intptr) <0x00011>
at (wrapper native-to-managed) Banshee.GStreamer.PlayerEngine.OnAboutToFinish (i
ntptr) <0x00054>

I need help to make GStreamer work with my Bluetooth AD2P Heathphones. I'm using Bluez (blue-manager) BTW.

Or at least, I need an advice to where I have to look or ask for help.


Regards.

---

### Post by Yellow Pasque on 2010-11-23
```
gconf-editor
```
Look at this path: /system/gstreamer/0.10/default/
Set the value of audiosink, chataudiosink, and musicaudiosink to "alsasink"
That may help.

---

### Post by Sergius14 on 2010-11-23
Definitely it worked!

audiosink already has "alsasink", but then I changed the other two's and started to work everything.

Thank you very much.

I really appreciate your help!

---

