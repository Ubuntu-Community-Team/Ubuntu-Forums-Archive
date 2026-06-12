---
title: "Setting up a 56k connection"
date: 2005-03-13
forum: Networking &amp; Wireless
---

### Post by The Dark one on 2005-03-13
Hullo...
I'm kinda new to linux, and I wonder how in the whole world i can configure an internet connection to my ISP with my 56k.modem??? Linuix has registered the modem as a functioning 56kfaxmodem, but i can't find the way to configure an internet connection! someone please help  :mrgreen: !

---

### Post by Ptero-4 on 2005-03-13
[QUOTE=The Dark one]Hullo...
I'm kinda new to linux, and I wonder how in the whole world i can configure an internet connection to my ISP with my 56k.modem??? Linuix has registered the modem as a functioning 56kfaxmodem, but i can't find the way to configure an internet connection! someone please help  :mrgreen: ![/QUOTE]
 in the terminal type:
sudo pppconfig
Enter your password (the one you created during the installation process).
And follow the on-screen instructions.
Then use pon to connect and poff to disconnect (or use the GNOME modemlights applet).

Hope this helps

---

