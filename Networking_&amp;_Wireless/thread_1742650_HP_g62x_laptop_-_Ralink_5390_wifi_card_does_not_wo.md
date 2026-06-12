---
title: "HP g62x laptop - Ralink 5390 wifi card does not work with ubuntu"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Belinrahs on 2011-04-29
I recently bought a HP g62x laptop for myself. It sports a decent Core i3 processor, 4 gigs of RAM and a 500GB HDD. It also came with Wireless-N, a real bonus because I am using a Wireless-N router. The chipset is a Ralink 5390. It came preinstalled with Windows 7, and everything works fine in there (obviously). 

I then proceeded to install Ubuntu 10.10 x64 a few days ago (this is before Natty came out) and everything worked . . . except WLAN. So I plugged in via Ethernet and went looking and found that I clearly wasn't the first to discover this issue. I found a guide [here]("http://ubuntulinux.co.in/blog/ubuntu/wifi-card-ralink-5390-configuration-in-ubuntu-10-10-64-bit/") that I followed to download the Ralink Linux driver (which is stated to support my chipset), configure, compile, and install. Everything went perfectly, I restarted; lo and behold, I have a list of access points. I went to connect to mine, entered the password, and now the animated "WiFi wave" logo keeps going indefinitely until you click it, and it freezes for a few minutes. It will unfreeze if you let it sit but clicking it causes the same freeze again.

I couldn't really care less about a WiFi icon freezing, but a.) it freezes everything else in the system up, not just the icon, and b.) it never actually completes the WiFi connection. Anyone knowledgeable in fixing issues like these that has an idea what to do, I would really appreciate it! I really, really don't want to be forced to use Windows because of a crappy WiFi driver!

**Since Natty came out I installed that and I can't even compile the driver without fatal errors, so I reverted to 10.10 and everything is the same as it was before. Note that this is a clean Ubuntu 10.10 Desktop Edition 64-bit install, nothing updated/modified/changed besides (attempting) to install this driver.**

---

### Post by Belinrahs on 2011-04-29
I have reached success -- on Natty! If you have the exact same problem I had, please follow this link:

[http://askubuntu.com/questions/38143/ralink-5390-card-in-laptop-does-not-work-after-installing-driver](http://askubuntu.com/questions/38143/ralink-5390-card-in-laptop-does-not-work-after-installing-driver)

Thank you!

---

