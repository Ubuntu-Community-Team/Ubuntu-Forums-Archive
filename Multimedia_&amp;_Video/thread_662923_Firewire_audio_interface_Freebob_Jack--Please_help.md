---
title: "Firewire audio interface_Freebob_Jack--Please help set-up"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by david424 on 2008-01-09
I am a Linux novice working with Gutsy.  Please help me to get Gutsy and PureData to recognize my Focusrite Saffire.  

my situation so far...  The following Packages are installed (using Synaptic):

jack
jackd
jackeq
jack-rack
jack-tools
libfreebob0
libfreebob0-dev
libjack0
libjack0.100.0.0
libjack0.100.0-dev
libjacksyn0
libjacksyn-dev
libjack-dev

When I open a terminal and type

jackd -d freebob

I get:

jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.

Then my Saffire gives the tell-tale click that seems to indicate that it is functioning.

When I open a second terminal and type

qjackctl

I get:
Warning: no locale found: /usr/share/locale/qjackctl_EN_CA.utf-8.qm

 Then the JACK Audio Connection Kit panel opens.  It is active and the Saffire input / outputs show up on the patchbay.

HOWEVER... neither PureData nor the Totem Movie Player give me the option of choosing Jack, Freebob or Saffire as audio outs.  And the Saffire does not register in the System>Preferences>Sounds or Multimedia Systems Selector menus.  Nor is it found when I run test.

Please help me... I know I'm close!

---

### Post by david424 on 2008-01-14
bump

---

