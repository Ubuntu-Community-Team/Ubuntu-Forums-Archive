---
title: "Latencyu issues for router running on USB"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by biofoder on 2010-11-15
I have configured my server so that it will act as a wireless router. My setup is as follow:

Bridged wlan0 and eth0 interface in LAN (bridge utils)
ppp0 getting internet from a mobile broadband modem (wvdial)
ufw as firewall
dnmasq for dhcp and dns
hostapd for wireless

The OS is the 64-bit server version of Maverick, running on  a extremely slow USB 2.0 memory stick (Kingston Traveler, cheapest there is, the write/read speed is just terrible. The reason for running the OS from USB is due to lack of available SATA ports on my MoBo.

My question to you is, will the write and read speed induce latency and affect the performance when routing my packets from the internet, compared to if I was running the OS on a SSD/SATA-drive? Any other performance issues you can think of by running on a USB? I'm not used to mobile broadband connections, and have no idea if the response time I experience is placebo or not.

---

