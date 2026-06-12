---
title: "Flash sound delayed in Firefox/Seamonkey"
date: 2018-03-27
forum: Multimedia Software
---

### Post by pcfan1234 on 2018-03-27
Hello,

I have Lubuntu 17.10 x64 on several machines (one has 2 Xeons, GeForce 210 and a Sound card, so not to slow for tiny flash-games).
on every computer the sound of flash is delayed for 1/2 sec. 
I can reproduce that in Firefox, Seamonkey and with the Firefox included with Tor. All the same
On Windows the flash content works correctly.
Other sounds (from Firefox HTML5, VLC) are normal.
In Google Chrome or Chromium with Pepper-based Flash it's also fine.



```

Flash:
flashplugin-installer/artful-updates,artful-security,artful,now 29.0.0.113ubuntu0.17.10.1 amd64 [installed]
  Adobe Flash Player plugin installer
Alsa:
ii  alsa-base                                     1.0.25+dfsg-0ubuntu5                            all          ALSA driver configuration files
ii  alsa-oss                                      1.0.28-1ubuntu1                                 amd64        ALSA wrapper for OSS applications
ii  alsa-utils                                    1.1.3-1ubuntu1                                  amd64        Utilities for configuring and using ALSA
ii  alsamixergui                                  0.9.0rc2-1-10                                   amd64        graphical soundcard mixer for ALSA soundcard driver

Pulse:
ii  gstreamer1.0-pulseaudio:amd64                 1.12.3-1ubuntu1                                 amd64        GStreamer plugin for PulseAudio
ii  projectm-pulseaudio                           2.1.0+dfsg-4build1                              amd64        projectM PulseAudio module
ii  pulseaudio                                    1:10.0-2ubuntu3.1                               amd64        PulseAudio sound server
ii  pulseaudio-utils                              1:10.0-2ubuntu3.1                               amd64        Command line tools for the PulseAudio sound server



```

If you need further information, please tell me.

Kind regards

pcfan1234

---

### Post by &amp;KyT$0P# on 2018-03-27
Use the Pepper Flash plugin with freshplayerplugin wrapper.

freshplayerplugin is available in the standard Ubuntu repositories -
```
sudo apt-get install browser-plugin-freshplayer-pepperflash
```

---

### Post by pcfan1234 on 2018-03-27
It worked.
But I am interest in why the flashplugin-installer won't work well.

---

