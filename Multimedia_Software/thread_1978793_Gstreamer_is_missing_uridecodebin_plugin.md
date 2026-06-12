---
title: "Gstreamer is missing uridecodebin plugin"
date: 2012-05-12
forum: Multimedia Software
---

### Post by peterdm on 2012-05-12
Gstreamer is missing the uridecodebin plugin. The plugin is supposed to be provided by gstreamer0.10-plugins-base, which I have installed, but for some reason it's totally broken. As a result, I can't play MKV. In fact, I probably can't play anything but I only tried MKV.

I tried
[LIST]
[*]Reinstallation of all gstreamer plugins
[*]Deinstallation of gstreamer-plugins-bad, because I've read reports that it breaks gstreamer in precise
[/LIST]

All to no avail. Any other ideas?

---

### Post by peterdm on 2012-08-07
The solution is to remove the directory "~/.gstreamer-0.10/".

---

