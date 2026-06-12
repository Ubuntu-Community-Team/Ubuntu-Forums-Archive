---
title: "Trying to navegate with sim card in HP 6735b"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by tanuii on 2009-09-10
Hi
I just installed latest version of ubuntu in a HP 6735b. This laptop comes with an integrated 3g hsdpa modem, so you can insert your sim phone card to be able no navigate trhough internet.
The problem is I don´t know how to configure this connection or maybe I should download the driver to this integrated modem.
Definetly I have no idea what should I do.
WOuld be fantastic if somebody could help me.
Thanks a lot.
 
[EMAIL="taniaxgarcia@gmail.com"][COLOR=#444444]taniaxgarcia@gmail.com[/COLOR][/EMAIL]

---

### Post by steamboatsailor on 2010-01-11
I've upgraded a friends computer from vista to Karmic and used this post [http://debian.pastebin.com/f845b46c](http://debian.pastebin.com/f845b46c) to enable the internal 3G-modem.
However i didn't got udev to work so I did an quick'n dirty solution ant put the following into /etc/rc.local:

```
/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
```Right before the last ```
exit 0
```

---

