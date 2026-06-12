---
title: "Wireless printer installed but  wont print"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by halfhearted on 2010-06-20
I'm using Ubuntu 10.04 on a laptop in a wireless system at home. It's all working fine. I can browse the internet without any difficulties. The problem is that I cannot print to my HP Laserjet 1022nw. The IP for the printer is 192.168.2.2 and I can reach it (and print) from my windows machine. But, if I use the laptop it cannot reach the server at 192.168.2.2 and all print jobs freeze. It's odd because I used the Ubuntu network printer install AppSocket/HP JetDirect connection and it found the printer at socket://192.168.2.2:9100 and installed the correct Foomatic driver. But now the browser cannot get to 192.168.2.2 and it wont print. What am I missing? Thanks for any help.

---

### Post by halfhearted on 2010-06-20
Right the problem is that the wi-fi network has given the laptop the same IP number as the printer. Is it possible to change the IP number on the laptop (running Ubuntu 10.04)? The config file doesn't seem to have much in it. Can I use ifconfig to do this? Thanks for any help.

---

### Post by Bucky Ball on 2010-06-20
Open System->Administration->Network and set up a static IP in there (change configuration to 'Static').

You will probably need to switch off DHCP server on your router though, which means you will need to set all devices to static IP. Incidentally, are you using this driver?

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

### Post by halfhearted on 2010-06-21
Thanks very much for that. How do I find out which driver I'm using? Are they listed somewhere.

---

### Post by halfhearted on 2010-06-21
Sorry but System>Administration>Network Tools does not me permit me to change anything, it just reports back on the current settings. You cannot change them using this applet. Is there another one?

---

### Post by Bucky Ball on 2010-06-21
Not network tools, just 'Network'. Should be directly above it unless they've changed that in 10.04.

Also, it appears as if 10.04 has HPLip by default. Use that to configure the printer.

[http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

