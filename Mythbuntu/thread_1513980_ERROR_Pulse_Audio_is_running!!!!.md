---
title: "ERROR: ***Pulse Audio is running!!!!***"
date: 2010-06-20
forum: Mythbuntu
---

### Post by psankovic on 2010-06-20
Hi,

I installed fresh mythbuntu 10.04 on my htpc. I upgraded alsa due to some sound problems. Now I have following error on boot, and myth will not start


2010-06-20 15:27:56.298 MythUI Image Cache size set to 20971520 bytes
2010-06-20 15:27:56.375 AudioPulseUtil, Warning: Can not connect to sound server, can not suspend.
			Connection refused
2010-06-20 15:27:56.375 ERROR: ***Pulse Audio is running!!!!***
2010-06-20 15:27:56.375 ERROR: But MythTV was not able to suspend it. EXITING!
2010-06-20 15:27:56.375 Deleting UPnP client...

Please help?

---

### Post by kja999 on 2010-06-23
Hi,

Myth doesn't like pulseaudio, and you seem to have managed to install it somehow.
Normally, I think, myth when launching will try and suspend pulse if its present (there is a tool called pasuspender). This seems to be the cause of your error.
Essentially you need to get rid of pulseaudio to make myth happy (sudo apt-get remove pulseaudio).

(There was lots of debate in the dev forums about myth running with pulse, but the upshot was its bad as it adds to sound latency).

---

### Post by LowSky on 2010-06-23
How did you update ALSA?

Secondly, kjA999, Ubuntu uses PulseAudio by defaut since 8.04. ALSA is still installed to act as a bridge for programs that do not have native support.

---

### Post by jyavenard on 2010-06-24
> **LowSky said:**
> How did you update ALSA?

Secondly, kjA999, Ubuntu uses PulseAudio by defaut since 8.04. ALSA is still installed to act as a bridge for programs that do not have native support.

??

that doesn't make sense...
ALSA will always have to be installed. Without alsa, Pulse wouldn't work..

There seems to be a great confusion between what Pulse and Alsa really are..

PulseAudio is an audio server, it relies on having either OSS or ALSA to actually access the audio hardware.

Also, Mythbuntu doesn't install pulseaudio by default.

To the OP...
Run pulseaudio --kill, pulseaudio --start before starting mythfrontend, this will restart the pulse server , and myth should be able to suspend it later.

---

