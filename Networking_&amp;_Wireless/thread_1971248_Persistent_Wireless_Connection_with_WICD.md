---
title: "Persistent Wireless Connection with WICD"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by cubemike99 on 2012-05-02
Hello. I'm trying to connect an old computer I have to my wireless network with a USB WiFi card. By some miracle, I have already been able to successfully use ndiswrapper to load the correct driver and can successfully connect with the iwconfig method and the wicd-cli method (did I mention the install is cli only?). My only complaint is that these methods are not persistent, that is, the connection has to be established manually on every boot. With wicd-gtk on a different install I was able to easily enable automagic connection on boot. Unfortunately, the man page is none too helpful. I believe I have to save the connection profile with the -w flag, but no comination of parameters seems to work. Thanks for all help.

---

