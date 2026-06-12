---
title: "Wireless settings lost on reboot"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by gruff on 2009-04-24
Since upgrading to 8.10 (and subsequently to 9.04) the wireless settings must be re-applied after each reboot. I have to run the following sequence of commands to get the connection working again after each reboot:

```
sudo iwconfig eth1 essid dlink
 
sudo iwconfig eth1 enc off

sudo iwconfig eth1 key off

```

In short, I must re-set the SSID and switch encryption off every time (this is deliberate since my router is faulty and only works un-encrypted)

How do I get Ubuntu to remember the settings? The Network Connections dialog has a similar problem - any changes made are not saved.

I did not have this problem in Heron and previous versions.

---

