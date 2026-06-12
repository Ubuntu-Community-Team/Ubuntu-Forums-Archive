---
title: "Pulseaudio Not Loading On Startup"
date: 2013-01-09
forum: Multimedia Software
---

### Post by Precipitous on 2013-01-09
Recently Pulseaudio has stopped loading at system startup. Once I get booted to a desktop I can launch it via a command window and it runs fine. In looking at the startup applications in etc/xdg/autostart  I noticed that both pulseaudio.desktop and pulseaudio-kde.desktop are present.  Could this be the source of the problem? If so, what is the best way to disable pulseaudio-kde.desktop from running at system startup so that I can easily re-enable it if need be?

---

### Post by Precipitous on 2013-01-10
In case anybody else has experienced this problem, I was able to resolve it by entering  [COLOR=Red]autospawn = yes[/COLOR]  in [COLOR=Navy]~/.pulse/client.conf[/COLOR]

---

### Post by Jannay on 2013-03-10
This solved my problem. Thanks!

---

