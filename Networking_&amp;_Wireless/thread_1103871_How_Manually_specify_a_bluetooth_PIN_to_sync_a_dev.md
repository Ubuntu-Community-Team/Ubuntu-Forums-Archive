---
title: "How? Manually specify a bluetooth PIN to sync a device"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by weblordpepe on 2009-03-23
Hello.

The Ubuntu bluetooth wizard tool thing allows me to sync up bluetooth devices quite nicely. **Provided I can enter a pin on my device**.

The problem is - my device is a GPS device which has its own pin that it likes to use. It has no buttons on it at all. Ubuntu finds the device perfectly, but when it comes to syncing -  Ubuntu just generates a random pin and expects me to enter it on my device. The result is my device won't talk to Ubuntu.

There are howto guides for bluetooth/gps but they all seem to like using low-level stuff which seems to break or not be accessible to anything else (eg gnome).
[LIST]
[*]Is there any way I can manually specify my little GPS device's MAC address and PIN?
[*]Where is the config file for the bluetooth wizard thingie? Perhaps I can enter a MAC/PIN combo there?
[/LIST]

---

### Post by Hobgoblin on 2009-03-24
Install [Blueman](https://edge.launchpad.net/~blueman/+archive/ppa) in place of bluez-gnome.

---

