---
title: "Ubuntu will not accept my WPA password."
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by jallenscott on 2010-01-07
Hi, sorry if this has already been asked, but anything that seemed to maybe be related was above my ability level with Ubuntu. I installed Ubuntu 9.10 on a second hard drive that I occasionally swap out for my laptop. However, when I attempted to connect to my wireless network, it would not take my password, and I made sure I had it written down correctly. I tried for half an hour to no avail to get it to work, the wireless icon would spin as though it were attempting to connect for several minutes, then it would either prompt me for the password again or just say the wireless network had been disconnected. My router is a D-Link Dir-655 Wireless N and the wireless card built into my Dell XPS M1530 is an Intel Wireless WiFi-Link 4965AGN. If anyone has any help, it would be greatly appreciated.

---

### Post by iponeverything on 2010-01-07
> **jallenscott said:**
> Hi, sorry if this has already been asked, but anything that seemed to maybe be related was above my ability level with Ubuntu. I installed Ubuntu 9.10 on a second hard drive that I occasionally swap out for my laptop. However, when I attempted to connect to my wireless network, it would not take my password, and I made sure I had it written down correctly. I tried for half an hour to no avail to get it to work, the wireless icon would spin as though it were attempting to connect for several minutes, then it would either prompt me for the password again or just say the wireless network had been disconnected. My router is a D-Link Dir-655 Wireless N and the wireless card built into my Dell XPS M1530 is an Intel Wireless WiFi-Link 4965AGN. If anyone has any help, it would be greatly appreciated.

No need for apologies. I would paste the wireless password directly from from the device into a text file and use USB thumb drive to transfer the text file to ubuntu install where you can just paste in the password, just so you rule out mistyping. After you rule that out, open terminal to watch the log messages while its trying to connect:

```
sudo tail -vf /var/log/messages /var/log/syslog
```

Hit Ctrl-c to stop monitoring the logs.

---

