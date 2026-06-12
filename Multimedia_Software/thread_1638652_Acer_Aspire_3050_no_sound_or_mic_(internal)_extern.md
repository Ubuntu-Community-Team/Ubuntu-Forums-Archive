---
title: "Acer Aspire 3050 no sound or mic (internal) external sound ok"
date: 2010-12-05
forum: Multimedia Software
---

### Post by francoisblake on 2010-12-05
Good morning

I installed Ubuntu 10.04, my sound works with my speakers plugged in but the internal speakers don't work nor the internal mic.
I've tried the following posts but still nothing.
[http://ubuntuforums.org/archive/index.php/t-1533332.html?pda=1]("http://ubuntuforums.org/view-source:http://ubuntuforums.org/archive/index.php/t-1533332.html?pda=1")
[https://help.ubuntu.com/community/HdaIntelSoundHowto?action=fullsearch&amp;context=180&amp;value=linkto%3A%22HdaIntelSoundHowto%22]("http://ubuntuforums.org/view-source:https://help.ubuntu.com/community/HdaIntelSoundHowto?action=fullsearch&context=180&value=linkto%3A%22HdaIntelSoundHowto%22")

**uname -a**
Linux francois-laptop 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[B]dpkg -l | grep "alsa"
[/B]ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
[B]
head -n 1 /proc/asound/card*/codec#* [/B]
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 2bfa

==> /proc/asound/card0/codec#1 <==
Codec: Realtek ALC883

Thank you

---

