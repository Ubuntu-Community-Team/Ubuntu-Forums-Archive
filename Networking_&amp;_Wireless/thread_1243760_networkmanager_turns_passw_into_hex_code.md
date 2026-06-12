---
title: "networkmanager turns passw into hex code ?"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by m41k on 2009-08-18
Wifi used to work without problems on ubuntu 8.10.
Now using 9.04 i am unable to connect. :confused:
It tries to connect and a popup window asks for wireless network authentication.
When i tick the 'show password' box my password has been replaced by hex code :confused:
I hope someone knows how to correct this, or how to connect without using the networkmanaper applet.

---

### Post by sergiom99 on 2009-08-18
I use Wicd instead of NM. Works WAY better. I also read somewhere that NM was broken in JJ for WPA2 networks.

```
 sudo apt-get install wicd
```
Good luck!

---

### Post by spd106 on 2009-08-18
You shouldn't worry too much, it will work with this hex form. This is a bug and it's been fixed upstream, so presumably it will be in Karmic (9.10).

See [http://blogs.gnome.org/dcbw/2009/05/12/i-was-told-thered-be-cookies/](http://blogs.gnome.org/dcbw/2009/05/12/i-was-told-thered-be-cookies/)

---

