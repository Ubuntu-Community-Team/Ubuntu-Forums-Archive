---
title: "Where is the configuration file for network (eth0,pppoe)"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by colau on 2009-05-07
Hi,
I added a manual wired connection from nm-connection-editor putting the ip address manually. 
But from the gnome-nettool selecting the eth0 got the ip 127.0.0.1 for eth0.
Why is it?

And where are the network configuration files for eth0 and pppoe?

And why does the nm-connection-editor shows the cross sign all the time?

I connect to internet using pppoeconf.
During browsing, every now and then the loading stops.
ping [www.google.com](www.google.com) from terminal does not work then says
ping: unknown host [www.google.com](www.google.com)

Then I re-adjust running ppoeconf.But this added extra pppoe in gnome-nettool.
Can anyone give some idea?

---

### Post by Iowan on 2009-05-07
> **colau said:**
> And where are the network configuration files for eth0 and pppoe?Interesting question.  I just put Jaunty on my laptop - so far it works (but I haven't tried wireless yet).  The "usual" place (*/etc/network/interfaces*) has only setup for "lo", and */etc/NetworkManager/nm-system-settings.conf * doesn't contain the information I had expected to find, either.

---

### Post by modmadmike on 2009-05-07
> **Iowan said:**
> Interesting question.  I just put Jaunty on my laptop - so far it works (but I haven't tried wireless yet).  The "usual" place (*/etc/network/interfaces*) has only setup for "lo", and */etc/NetworkManager/nm-system-settings.conf * doesn't contain the information I had expected to find, either.

(*/etc/network/interfaces*) is were mine are.

---

### Post by Iowan on 2009-05-13
I now have an "auto eth0", a "Manual eth0" and a wireless connection, but the information is not in /etc/network/interfaces - nor in /etc/NetworkManager that I've found.

---

### Post by Brandon Williams on 2009-05-13
Information about the interfaces that network manager handles is stored in gconf. Look in /system/networking/connections/ to find the gconf keys that are used. I'm not sure whether everything is there, but most of it is.

If you use /etc/network/interfaces to configure your interfaces, then network manager will ignore them, so the info won't show up in gconf, and network manager may even indicate that you don't have connectivity.

---

