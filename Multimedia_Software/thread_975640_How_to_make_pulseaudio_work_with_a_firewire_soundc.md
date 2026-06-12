---
title: "How to make pulseaudio work with a firewire soundcard on intrepid"
date: 2008-11-08
forum: Multimedia Software
---

### Post by DARKAD on 2008-11-08
I installed the pulseaudio-module-jack from:
[http://packages.debian.org/sid/pulseaudio-module-jack](http://packages.debian.org/sid/pulseaudio-module-jack)

after i added in /etc/pulse/default.pa
these two lines:

load-module module-jack-sink
load-module module-jack-source

after this line:
#load-module module-pipe-sink

so I start jack with no problem.

but when I enter pulseaudio on the console I get this result:

W: ltdl-bind-now.c: Failed to find original dlopen loader.

On the qjackctl control panel I see Pulseaudio Jack source among the input ports but I don't see the jack sink among the Output ports.

Any suggestion?

---

