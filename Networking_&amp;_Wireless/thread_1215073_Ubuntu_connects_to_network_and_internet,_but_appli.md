---
title: "Ubuntu connects to network and internet, but applications won't connect"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by michael1384 on 2009-07-16
Earlier today I was on the computer using Windows and the entire thing crashed. I rebooted it to find the network had stopped working. After turning it off at the plug this time, it started working again. Windows started using it again pretty easily, but Ubuntu thew a tantrum. It connects but none of the applications connect, could this be because the network has a different name now?

EDIT: If I can't fix it, I'll have to reinstall Ubuntu, and my sister will loose her bittorrent download and will kill me. Also, I can't ping.

---

### Post by superprash2003 on 2009-07-17
post output of the following
1)ifconfig
2)ping 208.67.222.222
3)ping google.com

---

### Post by martinbaselier on 2009-07-17
What do you mean with : "it connects, but none of the applications connect" ?

btw: It's wiser to put /home on it's own partition. This will prevent data loss if you have to reinstall. Keep in mind though that most of the settings are in the home directory too. But for a problem like this, it's not wise to reinstall the whole system. You could always purge and reinstall one application if it's causing problems and you can't find the cause.

---

