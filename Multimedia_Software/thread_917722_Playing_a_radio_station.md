---
title: "Playing a radio station"
date: 2008-09-12
forum: Multimedia Software
---

### Post by linuxwalleye on 2008-09-12
Hey Ubuntu experts, can anybody tell me what I need to install to be able to play this radio station link in Firefox?

[http://gateway.andohs.net/player/default_noax.aspx?nid=2920&sid=1352&customlogo=](http://gateway.andohs.net/player/default_noax.aspx?nid=2920&sid=1352&customlogo=)

Thanks

---

### Post by gandaran on 2008-09-12
tried it, works fine with the totem plugin, you just need to install the gstreamer plugins (codecs), look for them in synaptic package manager or install the ubuntu-restricted-extras packages
code: **sudo apt-get install ubuntu-restricted-extras**

---

### Post by linuxwalleye on 2008-09-12
That did the trick--thanks!!

---

