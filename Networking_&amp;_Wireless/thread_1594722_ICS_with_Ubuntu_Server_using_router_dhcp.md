---
title: "ICS with Ubuntu Server using router dhcp"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by biofoder on 2010-10-12
I have a server running Ubuntu connected to internet using a mobile phone with 3G (usb0) and to a wireless router (wlan0). How can I configure my server so that my router (D-Link DIR-655) can fetch the internet connection from my usb0 interface and share it to all computers and devices connected to my wireless network? All the tutorials out there only seem to explain how to set up ICS by creating a new local network without the use of a router, but I want the router to host the WLAN and take care of the firewall and DHCP. Also, most tutorials use the firestarter GUI, which is not an option running Ubuntu Server.

My setup:
usb0 uses dhcp to get 192.168.100.100 (internet connection)
wlan0 uses dhcp to get 192.168.0.100
Router located at 192.168.0.1

How would I achieve this? Using iptables? Setting my router to access internet from a static IP? I am in desperate need of your help, google has failed me big time. What's frustrating is that this is insanely easy to do on a Windows system, just checking a box in the network settings and voila, the entire network have access to internet. Why is this so darn difficult to do in Ubuntu?

---

