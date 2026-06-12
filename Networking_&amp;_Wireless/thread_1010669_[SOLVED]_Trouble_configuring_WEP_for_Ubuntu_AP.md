---
title: "[SOLVED] Trouble configuring WEP for Ubuntu AP"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by squeakysystem on 2008-12-14
I'm trying to set up my Ubuntu box as a wireless access point, using Madwifi and an Atheros AR5212/5213 PCI wireless card. After much fuss, I've got it working so that my other machines can connect to the Ubuntu box, with DHCP, etc.

Problem: I cannot figure out how to enable WEP, so that clients need to provide a password when they connect to my AP. 

I've tried adding various things to "/etc/network/interfaces":

	wireless-key 1234-1234-1234-1234

or

	wireless-key open 1234-1234-1234-1234

or

	wireless-key restricted 1234-1234-1234-1234

...but the access point is still open.

I'd like to use 128-bit WEP. I know that WPA is better but it's been such a hassle to even get this far that I'll just settle for WEP now. Once that works, I'll worry about WPA later.

Any suggestions/pointers/tips?

---

### Post by squeakysystem on 2008-12-14
Problem SOLVED: after reading many posts on the net, I found that in order for the "wireless-key" directive in the /etc/network/interfaces file to be processed correctly, I needed to auto-create the access point, like this:

# echo "options ath_pci autocreate=ap" >>/etc/modprobe.d/options

I don't really understand why this works, but it solved my problem.

---

