---
title: "ALSA Config. Question Multiple Devices"
date: 2011-06-22
forum: Multimedia Software
---

### Post by jeffjungletech on 2011-06-22
Problem which needs to be solved:
-=-=-=-=-=-=
Capture audio from multiple devices (on-board internal mic./line in, USB mic. etc...) and mux/merge into one stream/device. Plug'n'play support is also a must. (If a USB mic. is unplugged and another one is plugged in there must be a way by which to re'init the system so that it detects the changes). 


-=-=-=-=-=-=
Must have's:
-=-=-=-=-=-=
System must be able to interface with java in such a way that using the java native TargetDataLine audio capture of the mixed/muxed/merged stream works. (Open to alternatives, byte stream (ByteBuffer) of captured audio data within java without using native TargetDataLine is an option)



OS: Ubuntu 10.10 (2.6.35-28-generic-pae #50-Ubuntu i686 GNU/Linux)
Java Version: latest

Approaches taken:
-=-=-=-=-=-=
JackD with JJack
-=-=-=-=-=-=
[http://www.jackaudio.org/](http://www.jackaudio.org/)
[http://jjack.berlios.de/](http://jjack.berlios.de/)

Issue, jjack client and *.so are not updated to use the latest jackD server. Using version one of jackD  and related JJack, all audio captured within Java is silent. JackD has multiple x-runs, jjack and jackd don't connect.

-=-=-=-=-=-=
ALSA
-=-=-=-=-=-=
[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)
[https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture](https://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture)
[http://alsa.opensrc.org/Udev](http://alsa.opensrc.org/Udev)
[http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html#pcm_plugins_dmix](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html#pcm_plugins_dmix)

Issue, device wasn't ever setup due to configuration issues.

So, the next idea is to some how configure ALSA so that all 'capture'/input devices are place into one virtual card, after which, JACK is launched and told to use this new virtual card. Is this possible?

---

### Post by Capoeira on 2011-08-22
did you manage to make java conect to jack?

I tried loopback device, but it has some issues

---

