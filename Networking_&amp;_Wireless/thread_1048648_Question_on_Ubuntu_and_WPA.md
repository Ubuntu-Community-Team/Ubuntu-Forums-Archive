---
title: "Question on Ubuntu and WPA"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-01-23
Hi. I use WEP(my modem wont support WPA). I'd like to know if other Ubuntu users have any trouble setting up WPA in Ubuntu or is it just as easy as WEP?

---

### Post by deadtom on 2009-01-23
I've been told that network manager handles it beautifully although I've never personally been able to get it to work.
Using wpa_supplicant works if it supports your NIC drivers but is a real pain to set up.

It can be done. :)

---

### Post by deadtom on 2009-02-17
I installed wicd just a few minutes ago. It took no tweaking, no screwing around and connected to my WPA2/TKIP router with no problems at all whereas Knetworkmanager wouldn't even see it and would puke all over itself every time I tried to manually connect it.
If you are still working on this issue you might try it. There are good instructions here:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

In the section that explains installing for ubuntu, I just replaced "hardy" with "intrepid" in the apt-get command, since that's the version I'm using, and everything went fine.

---

### Post by Rytron on 2009-02-17
Thanks deadtom.

---

### Post by Rytron on 2009-09-05
I now use WPA on a new modem/router. All works fine.

---

