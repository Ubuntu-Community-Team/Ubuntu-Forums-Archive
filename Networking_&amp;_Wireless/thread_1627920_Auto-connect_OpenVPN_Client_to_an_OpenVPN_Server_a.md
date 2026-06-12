---
title: "Auto-connect OpenVPN Client to an OpenVPN Server at start-up"
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by carlexpc on 2010-11-22
Hi!

I would like to make one of my client PC connect to an OpenVPN Server automatically at start-up via an OpenVPN client. My client PC is not running any GUI so I need to connect to a VPN via command-line. 

How will I do this? 

TIA

---

### Post by carlexpc on 2010-11-22
I have found the solution to my problem. I'll share with you what I did.

1. I saved all the .pem files and the openvpn client config file to /etc/openvpn.

2. I edited /etc/default/openvpn and enabled AUTOSTART setting its value to
AUTOSTART=all.

I rebooted my pc and checked if my client has connected to the openvpn server and it worked.

---

### Post by Ufoeke on 2011-06-09
Thank you :)

It worked for me aswell

---

### Post by jerryvdv on 2011-07-08
Hey 
I was hoping to do the same thing.
Only thing I can't figure out right now is how to handle user/password authentication..
Any ideas?

---

