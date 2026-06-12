---
title: "Using laptop as internet source for PC (just a little smudgeon of help please!)"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by Xog on 2010-01-19
Let me catch you up to speed.

I have:
I have a wireless router.
I have a laptop that can connect to the wireless router.
I have a PC that is currently wired to my laptop.
I have edited sysctl.conf and uncommented net.ipv4.ip_forward=1 (on the laptop)
I have done "sysctl -a"

I need:
I need to have the PC connect to the internet using the wireless from my laptop.

For reasons beyond my control I cannot move my PC to the router or modem for easier wired access. After I have internet and have run a few programs I can undo all of this and access it wirelessly from the PC.

Please advise,
Thank you.

Edit: Some progress with the help of a professional. Unfortunately he was helping me through AIM and it was a little difficult and we are still unsuccessful but making progress.

Laptop's 'Auto eth0'
IPv4 Settings: 
Method: Manual
Address: 10.1.1.1
Netmask: 255.255.255.0
Gateway: 0.0.0.0

PC's 'Auto eth0'
IPv4  Settings:
Method: Manual
Address: 10.1.1.2
Netmask: 255.255.255.0
Gateway: 10.1.1.1

The two computers can ping eachother.
The laptop can ping the router.
The laptop can ping the PC.
The PC can ping the laptop and router.
The PC can ping 4.2.2.1.
The PC cannot open webpages.

I install dnsmasq

laptop can ping PC
PC can't ping anything.

Going to bed. 3:15 AM. Someone please help.

---

### Post by Xog on 2010-01-19
bump

---

### Post by Xog on 2010-01-19
Bump- at work and will try any solutions provided when i get home

---

