---
title: "EDUP Wireless Adapter not connecting to router"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by mehta on 2010-01-03
For several months I was using EDUP adapter with both my laptop that operated on Ubuntu 9.04 exclusively and a desktop that could also boot with XP. Soon after 9.10 was released I updated my laptop and was able to use the adapter to connect to the Net.
Recently, I also updated the desktop but also made it exclusively a Linux machine.  Unfortunately, I have been unable to get the wireless adapter to work again on the desktop.
The OS recognizes the device as wlan0, and lsusb shows:
Bus 003 Device 005: 0cde:0008 Z-Com Sitecom Wireless Network Adapter 100G+ WL -125
The network manager recognises the availability of the wireless network and attempts to connect.  After trying for a while it comes up with a dialog box "Wireless Network Authentication Required" and in response I enter the WPA password but with no success.
The behaviour would indicate that I am entering the wrong password but I am not.  I have checked it several times and compared with the password that works with the laptop.
Where am I going wrong?
The desktop is somewhat old and is an ACER Aspire

---

### Post by mehta on 2010-01-11
Reluctantly, I had to go back to 9.04 and all is well again.

---

### Post by coatl on 2010-03-04
I'm curious as to how you got your wireless card working on 9.04. I've got (appearently?) the same hardware, but it won't work for me after I've tried many times (on 9.04).

---

### Post by dirtfarmer on 2010-04-25
I've been trying to connect my edup card to to a router using dd-wrt for the past few hours and I finally got it to work. (the client is 9.10)

Initially I had the router's wireless channel configured to auto. When I tried to attempt to connect with my edup card it exhibited the same behaviour as you experienced.

I switched the router to broadcast on channel 5 (2.432GHz) and the wireless card immediately logged on and is now working. 

channel 5 is the first one I tried, maybe other's work.

---

