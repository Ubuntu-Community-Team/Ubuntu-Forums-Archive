---
title: "macchanger no longer works in 13.04"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by lasdin on 2013-05-16
[COLOR=#333333][FONT=Ubuntu Mono]I posted this as a bug in lubuntu-desktop, but also decided to ask here since I may be overlooking something. Here's the bug report:

After upgrading (fresh install) Lubuntu to 13.04, macchanger will not change the mac address for wlan0 on boot (eth0 works).
Adding the lines:
```
pre-up macchanger -e eth0
pre-up macchanger -e wlan0
```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]to _/etc/network/interfaces_ will hang boot times waiting for the network on 13.04. 12.04 will load fine with MACs changed.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]macchanger changes eth0 fine, and trying wlan0 in terminal reports "device or resource busy".[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Following this guide ([http://excid3.com/blog/random-mac-address-on-start-up-with-ubuntu/#.UZUyOSDLlCQ](http://excid3.com/blog/random-mac-address-on-start-up-with-ubuntu/#.UZUyOSDLlCQ)) in 13.04 works for eth0 but not wlan0:
```
ifconfig wlan0 down
iwconfig wlan0 mode monitor
/usr/bin/macchanger -e wlan0
ifconfig wlan0 up
```[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]I have tried running software update, and the issue still persists.

For now I have rolled back to 12.10, but if anyone has any ideas on what I can test in 13.04 let me know![/FONT][/COLOR]

---

