---
title: "Wrieless issue"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by Unotforme on 2012-06-23
Hello everyone,

Like many here I've been having trouble with my wirelss connections dropping at random times. Needless to say it's driving me a little nuts. I've been trolling the forums trying to find different tidbits and solutions, but nothing pertains to my scenario, which to me means it is probably my network card or the modem/router, but I don't really know, as I don't know much about networking. I'm running Xubuntu 12.04

My setup is a cable (my ISP) connected to a Cisco DCP3825 Modem/Router connected to desktop by Ethernet 1 port (wired). Works fine. I have a laptop (Acer Travelmate 5530), 2 Android phones, 1 Blackberry phone, Kobo e-reader, and a Wii all accessing the wireless at different times. They all have no problem connecting to the wireless, however they all randomly lose the connection (no pattern as to when that I can ascetain); and I have to manually reconnect when this happens.

After running 'lspci' in Terminal, I've determined the Ethernet controller on my Desktop is Marvel Tech IEEE 88E8071 PCi-e (Rev16). I've managed to find a linux driver for the card (version 10.92.1.3 dated Jan26/12). It is for Kernel 2.6.x I don't really want to run this driver until I know if the card is actually the issue.

Any suggestions as to how I can troubleshoot this setup and fix this issue is greatly appreciated.

---

### Post by 54woody3 on 2012-06-24
Possibly the cache gets full and you need to reboot then router periodically  ..it worked for me.

---

### Post by Unotforme on 2012-06-27
Thanks. That is definitely an improvement, though I'm still having a few issues. Is there anywhere on the filesystem where I could wipe the internet cache manually, maybe that would help as well.

---

### Post by asmoore82 on 2012-06-27
Do you have the wireless configured to use a so called "hidden" or "cloaked" non-broadcasting SSID (network name)?

---

