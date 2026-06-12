---
title: "Flash plugin for Firefox: where can I find it?"
date: 2013-07-03
forum: Multimedia Software
---

### Post by Apolyonn on 2013-07-03
The title pretty much says it all.  I'm running Lubuntu minimum install with LXDE, which was downloaded post-install.

>inb4 "use Chromium elel"
>inb4 "wait 4 HTML5"

Failed attempts:
1) I tried installing flashplugin-installer.  Upon restarting Firefox, the video loads literally one second's worth of the video; then it crashes (the "tv static" error message pops up).
2) The "apt" on the Flashplugin page on the website is broken

Help would be appreciated

---

### Post by carl4926 on 2013-07-03
The flash plugin should get installed with the restricted extras
Or you can add it manually via synaptic

Older CPU's may not work with the current flash-plugin

---

### Post by Apolyonn on 2013-07-03
Upon a second glance, I found that the .tar.gz on Adobe's site worked for me.  It comes with a readme file, but here's a quick run-through.

Download and extract
Copy the .so file to /usr/lib/mozilla/plugins
Recursively copy the contents of the "usr" folder to your "/usr" folder

Working fine and with ALSA output.

tl;dr, solved.

---

