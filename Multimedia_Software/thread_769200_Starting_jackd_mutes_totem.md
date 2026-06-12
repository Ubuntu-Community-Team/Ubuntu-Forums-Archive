---
title: "Starting jackd mutes totem"
date: 2008-04-26
forum: Multimedia Software
---

### Post by stbub on 2008-04-26
On my system, I have an onboard intel audio and a PCI audio card (M-Audio Delta 66).

My default audio device is the onboard intel.

I start playing something with totem.  Things are ok.

I then start jackd on the PCI audio card, and totem becomes silent.

This used to work fine on Gutsy. But with Hardy, things don't work.

Any help appreciated.
Thanks,

---

### Post by stbub on 2008-04-26
Looks like if I kill pulseaudio, things work ok.

Should I care for pulseaudio?  And if so, how do I prevent it from breaking things for me?

---

### Post by jhnphm on 2008-04-27
You can edit the config file in /etc/pulse/default.pa to select which card pulseaudio uses. I'm assuming you're using qjackctl, so you have to run qjackctl.bin since qjackctl contains a wrapper to suspend pulseaudio. 

I think as an alternative to editing config files you can install padevchooser and tell applications which sound card to use via a GUI too.

---

### Post by stbub on 2008-04-27
> **jhnphm said:**
> You can edit the config file in /etc/pulse/default.pa to select which card pulseaudio uses. I'm assuming you're using qjackctl, so you have to run qjackctl.bin since qjackctl contains a wrapper to suspend pulseaudio. 

I think as an alternative to editing config files you can install padevchooser and tell applications which sound card to use via a GUI too.

Didn't notice qjackctl was a wrapper.  Thanks.

I ended up going to System->Preferences->Sound and chose ALSA for all.  This seems to render PulseAudio irrelevant, which is fine by me.

BTW, the qjackctl wrapper is buggy.  It should be:

pasuspender -- /usr/bin/qjackctl.bin "$@"

instead of:

pasuspender /usr/bin/qjackctl.bin "$@"

PS. At some point someone's going to have to decide to REMOVE instead of ADDING audio systems.  PulseAudio, jack, OSS, alsa, ... it's not getting any simpler :-)

Otherwise, the only hardy problem I have left is that the PATA on the jmicron ain't working.  But that's another story :-)

---

