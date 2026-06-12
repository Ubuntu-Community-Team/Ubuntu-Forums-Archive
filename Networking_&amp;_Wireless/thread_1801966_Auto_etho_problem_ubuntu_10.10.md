---
title: "Auto etho problem ubuntu 10.10"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by pranav.33 on 2011-07-11
I have Ubuntu 10.10 installed in my laptop. I'm not able  to connect it to the net through Ethernet cable. It says device not  managed. I'm able to connect and use the wireless without any issues though.

---

### Post by Iowan on 2011-07-11
From Code of Conduct:
> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

"Device not managed" frequently means the device is defined in */etc/network/interfaces*. If so, the lines can be commented out, and networking restarted (or reboot the machine) to see if it helps.

---

### Post by pranav.33 on 2011-07-12
[SIZE=3][SIZE=2]I tried doing that, but it says access denied. :([/SIZE]
[/SIZE]

---

### Post by jmoorse on 2011-07-12
> **pranav.33 said:**
> [SIZE=3][SIZE=2]I tried doing that, but it says access denied. :([/SIZE]
[/SIZE]

Use 'sudo gedit /etc/network/interfaces'

---

### Post by pranav.33 on 2011-07-12
> **jmoorse said:**
> Use 'sudo gedit /etc/network/interfaces'

That totally worked thanks :D

---

