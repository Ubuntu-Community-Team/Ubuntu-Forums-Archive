---
title: "&quot;eth0 device not ready&quot; when trying to share internet"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by Lichig0 on 2009-01-03
My desktop has Ubuntu Intrepid installed and it connects through wireless to get online. My old laptop however also has Ubuntu Intrepid installed, but unfortunately I don't have a wireless card for it quite yet.

So I plugged in my laptop to my desktop through an Ethernet cable and when I select the share internet connection in Firestarter I get

"Failed to start the firewall
The device eth0 is not ready."


How do I share my internet connection to my laptop through my desktop?

---

### Post by hoathuong on 2009-01-03
You must config eth0 on your desktop and laptop

---

### Post by superprash2003 on 2009-01-03
[http://ubuntuforums.org/showthread.php?t=234068](http://ubuntuforums.org/showthread.php?t=234068)

---

### Post by Lichig0 on 2009-01-03
"Ok, so the "eth0 not ready" issue was solved by assigning a static IP to it."

Instead of takeing guesses on how to do this I'm just going to ask, because I'm not too sure on how to go about doing that.

---

### Post by Iowan on 2009-01-04
Dunno if the static address bug in NM got solved, but [here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround.  Save removing NM for a last resort.

---

### Post by tednumber8 on 2009-01-04
what about when wlan0 wont work?

---

### Post by superprash2003 on 2009-01-05
same thing. use static ip

---

