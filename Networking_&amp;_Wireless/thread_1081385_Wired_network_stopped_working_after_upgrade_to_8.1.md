---
title: "Wired network stopped working after upgrade to 8.10"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by Dagur on 2009-02-26
I just did a clean install of 8.04 (since I had the CD) and upgraded straight to 8.10. End everythin worked fine during that process but when I restarted the computer after the upgrade, the networking was out. It doesn't seem to be able to obtain an IP from the router.

What can I do?

---

### Post by Asgar on 2009-02-26
I have the same problem, everything was ok on 8.04 until i installed 8.10. please help

---

### Post by Iowan on 2009-02-26
Check contents of */etc/network/interfaces* file. Start by saving a copy of the file, then commenting out anything but the "lo" definition and auto line. save and restart networking with **/etc/init.d/networking restart** from a terminal).

---

### Post by HyperHacker on 2009-02-26
Same problem with a Gateway MX7515 laptop. Since upgrading to 8.10, wireless still works but eth0 has ceased to exist. It's not listed in /etc/network/interfaces or ifconfig. When I enable networking I immediately get a "network disconnected" popup message.

---

### Post by Iowan on 2009-02-27
The new Network Manager works a bit differently in 8.10 than previous versions.  It has configuration files in /etc/NetworkManager, and does not use /etc/network/interfaces file.  Also, (unless something has changed recently) it will allow only one active interface - so if wireless is working, wireless won't.  I've read threads that suggest that if wired connection is plugged in, it will override (disable) the wireless connection.

---

