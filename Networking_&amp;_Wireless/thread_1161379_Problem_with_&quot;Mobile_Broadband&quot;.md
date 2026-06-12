---
title: "Problem with &quot;Mobile Broadband&quot;"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by nuuuuuuub on 2009-05-16
Hi, did somebody connect to the internet via bluetooth (mobile phone <-> bluetooth <-> notebook) in ubuntu 9.04 ?

tnx

---

### Post by Hobgoblin on 2009-05-16
Not tried with 9.04 but I have with 8.04 and 8.10

[This should still work.](https://help.ubuntu.com/community/BluetoothDialup)

---

### Post by nuuuuuuub on 2009-05-16
> **Hobgoblin said:**
> Not tried with 9.04 but I have with 8.04 and 8.10

[This should still work.]("https://help.ubuntu.com/community/BluetoothDialup")

thanks, i know this method, but i want to connect to the internet using a desktop programs (networks manager). For example, as well as in Mac OS.

I know that it is possible to connect to the internet using a bridge: mobile - USB-cabel - ubuntu. 
[[FONT=Arial][/FONT]]("http://eng-ukr.slovnenya.com/dictionary/method")

---

### Post by Hobgoblin on 2009-05-16
The pairing can be done through the GUI, you need to do the sections headed "Configuring the rfcomm device" and "Configuring PPP", these sections only need to be done once.
You can then use gnome-ppp to make the actual connection from the desktop as you would using DUN in Windows.

Or you can install [Blueman](https://edge.launchpad.net/~blueman/+archive/ppa) which will do everything from the GUI but I found the connection to be very unstable.

---

