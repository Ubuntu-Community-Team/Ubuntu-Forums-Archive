---
title: "Atheros 9285 in HP Probook"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by Hakoda on 2012-01-13
I have a HP Probook 4530s notebook with a PCI-E Atheros 9285. Upon the first reboot into Ubuntu 11.10, internet was blazing fast as it is on my Windows setup on the same computer. I did not choose to install updates during setup because I wanted to do them later, ran the Update Manager on my first reboot as planned. Rebooted and the internet was out. I can connect to my wireless network, networking is shown as working fine but when you attempt to browse the web you get a "Looking up google.com" message for about 2 minutes before it claims it can't connect to the server.

I'm fairly tech savy, however new to linux. Thank you in advance.

Router claims the OS is successfully connected, changing Ununtu's DNS Settings did not make a difference.

EDIT: Flushing DNS seemed to have fixed the problem. I did it using the following commands, needed to plug into ethernet first:
```

sudo apt-get install nscd 
[password]
sudo /etc/init.d/nscd restart

```

---

