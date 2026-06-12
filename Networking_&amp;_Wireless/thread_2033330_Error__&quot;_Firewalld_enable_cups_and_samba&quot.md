---
title: "Error  &quot; Firewalld enable cups and samba&quot;"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by motla68 on 2012-07-26
FIREWALLD PROBLEM :KS

SOLVED ! FIXED! 3 days of endless searches through forums on and off and changing configurations and it finally paid off, I figured this out on my own and everything came to life, automatically detected all my printers. I am fairly new to the linux community so please excuse the excitement.

Ubuntu 12.04 LTS OS install has an incorrect file name for network management. Use mv command

Old : /etc/NetworkManager/NetworkManager.conf

New: /etc/NetworkManager/nm-system-settings.conf

Network manager will need restarted or restart computer.

The only way I found this is because I have a older computer that will only run Ubuntu 10, just happened to see that they were different. I hope this will go up to the developers so they can make changes for the next updates. So glad this was found, because I would hate to lose Ubuntu 12, other then this problem it has been one of the best OSs I have used.

---

