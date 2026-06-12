---
title: "Compaq CQ60 Wireless using 11.04"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by hatewindows on 2011-10-07
Hello --I installed 11.04 Ubuntu on my notebook pc Compaq CQ60--Everything works great except i notice when different web pages are loading--The Blue wireless Button on the notebook--Keeps changing from Blue to Orange--It connects disconnects connects disconnects--So fast that the page still loads.. Does anyone know a fix for this? Thanks so much... Have a great eve..

---

### Post by wildmanne39 on 2011-10-07
Hi, there is a bug where some do that, they are not really disconnecting, the light just flashes.
Thank you

---

### Post by wildmanne39 on 2011-10-07
Hi, I did a quick search and it appears this may fix it.
[http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops](http://ubuntuguide.net/stop-the-blinking-wireless-led-light-on-ubuntu-10-10-laptops)
Thank you

---

### Post by hatewindows on 2011-10-08
Thanks so much i will give that command a try!!  Have a great day!! Thank you............

---

### Post by hatewindows on 2011-10-08
(gedit:1792): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XHU92V': No such file or directory

This is the error i see--when saving the file and rebooting..

---

### Post by wildmanne39 on 2011-10-08
Hi, you can get rid of that error by creating the file.
```
sudo mkdir -p /root/.local/share
```
Thank you

---

