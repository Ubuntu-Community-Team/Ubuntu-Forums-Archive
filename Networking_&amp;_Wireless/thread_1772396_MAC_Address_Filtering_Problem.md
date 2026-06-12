---
title: "MAC Address Filtering Problem"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by unknown01 on 2011-05-31
Hey guys:
Actually I have a problem with this MAC Filtering. I want to connect to a open network but I can't connect to it so I thought this problem is because of the MAC address filtering so:
First of all I Open a terminal and type in
```
airodump-ng (my interface)
```then i use this command to scan the specific open network that uses MAC Filtering 
```
airodump-ng -c (channel) --bssid (the bessid) --w (name) (my interface)
```then in the station I got a new BSSID
after that i stop this terminal and open a new terminal and use
```
ifconfig (my interface) down
```then I changed my MAC address to the station MAC address in the first terminal using this command
```
macchanger -m (station bssid) (my interface)
```then i choose connect but it says can't optain IP addresses.
what's the problem here?
Any Help highly appreciate.
My OS: Ubuntu 11.04
Sometimes uses : Backtrack 5 32bit Gnome

---

