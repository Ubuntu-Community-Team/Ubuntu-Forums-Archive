---
title: "(gutsy) Sound works for gaim but..."
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by triptoe on 2007-09-12
my sound for gaim works but nothing else is working... the logout and login sounds for system sounds don't work... and my flash videos on youtube don't play any sound. 

Is that because gaim uses alsa and the others use OSS? what do i do?

---

### Post by Gremlinzzz on 2007-09-12
Go into synaptic package manager and remove gaim and gaim data. then install the supported gaim called pidgin.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.1_Instant_Messenger](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.1_Instant_Messenger)

---

### Post by Gremlinzzz on 2007-09-12
* If sound doesn't work in Flash Player (for example on YouTube), then edit the configuration file: 

sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Change:

FIREFOX_DSP=""

to:

FIREFOX_DSP="aoss"

Restart Firefox. 
its all in the guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

