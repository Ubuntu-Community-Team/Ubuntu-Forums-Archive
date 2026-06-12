---
title: "Ubuntu 10.04 Wicd won't connect anymore"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by lisbonant on 2010-05-08
I just finished upgrading via the software upgrade application from 9.10 to 10.04.  On the first boot everything worked fine, network ran smoothly and entirely without hitches.  The only thing that bothered me was the lack of the volume control applet so I added that to the startup applications list and rebooted.  Now I can't get Wicd to connect, either wireless or wired.  I removed the volume control application and still had the same issue.  Does anyone know why this could possibly be occurring and/or how to fix it?

---

### Post by royleith on 2010-05-09
I have had a strange problem with wicd for some time before 10.04. When several wireless networks appear, clicking on connect ends in failure. However, clicking for automatic connection and rebooting is successful.

I discovered that, clicking on the network below the configured one will usually result in success. The progress line at the bottom of the window confirms that wicd is attempting to connect to the wireless network above the one you are trying to connect.

---

### Post by lisbonant on 2010-05-09
Interesting suggestion, didn't work for me, but whatever works, non?

Seems like the problem was DHCP-related, in case anyone's interested.  On a whim I set it to static IP and it works like a charm.

---

