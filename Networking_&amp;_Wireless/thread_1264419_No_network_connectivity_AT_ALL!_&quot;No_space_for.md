---
title: "No network connectivity AT ALL! &quot;No space for Tx&quot;"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by Rofko on 2009-09-12
Hi all

Getting desperate with this issue, which has appeared out of nowhere.

I have absolutely no connectivity - I have two wireless cards, one USB, one internal, both fully supported, and also a wired network. I cannot connect to ANY network in ANY way - wireless or wired.

dmesg gives this error:

iwl3945: No space for Tx
iwl3945: Error sending REPLY_SCAN_CMD: iwl3945_enqueue_hcmd failed: 28

Absolutely crucial I get this fixed ASAP. Anyone got any pointers? I can't find out what these errors mean.

Thanks

---

### Post by Rofko on 2009-09-12
BUMP! 

Really? No-one knows what this might be?? :'(

---

### Post by majorctin on 2009-09-12
Have you tried:
```
sudo /etc/init.d/networking restart
```I had same problem, no network connection at all (LAN/WLAN). I haven't done any configurations on my Ubuntu computers. My Windows machine had connection but both Ubuntu computers had no connection. I try that command and then reconnect to network and it helps, both Ubuntu computers get connection after restarting networking.

---

