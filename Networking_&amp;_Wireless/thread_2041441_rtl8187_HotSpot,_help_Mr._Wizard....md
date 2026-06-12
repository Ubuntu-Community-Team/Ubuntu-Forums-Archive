---
title: "rtl8187 HotSpot, help Mr. Wizard..."
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by aztecaa on 2012-08-12
Thanks for having this helpful forum for us who need to step up our game. Look forward to getting some help from you wizards!
I have my long range antenna connected to my rtl8187 and then to PC usb. 
  My question is...  How do I make it a HOTSPOT so I can connect to  wirelessly to use my iPad, Cel Phone etc..? 
I also want to put a ip  security camera outside for viewing.  :confused:

---

### Post by bakegoodz on 2012-08-12
First see if your adapter even does AP Mode
```
sudo apt-get install iw
iw list | grep modes: -A 10
```
If it lists "AP" mode you can setup HostAP. I like this guide:
[http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/](http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/)

---

### Post by aztecaa on 2012-08-12
> **bakegoodz said:**
> First see if your adapter even does AP Mode
```
sudo apt-get install iw
iw list | grep modes: -A 10
```If it lists "AP" mode you can setup HostAP. I like this guide:
[http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/](http://www.danbishop.org/2011/12/11/using-hostapd-to-add-wireless-access-point-capabilities-to-an-ubuntu-server/)

[COLOR=Navy]SoftAP Enable box at the bottom of the screen. Is that what you mean?[/COLOR]

---

### Post by bakegoodz on 2012-08-13
I searched for "SoftAP Enable box" to see what you were talking about. I only could find that some wireless adapters have Windows software that enables WiFi adapters to act as access points. That still will not tell whether the Linux driver for your WiFi adapter supports AP Mode or not.

---

