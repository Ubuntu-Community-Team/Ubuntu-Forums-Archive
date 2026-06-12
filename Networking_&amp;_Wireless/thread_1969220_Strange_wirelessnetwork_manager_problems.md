---
title: "Strange wireless/network manager problems"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by simpelmees on 2012-04-29
Hi everyone,

I recently installed Xubuntu 11.10 on an old medion pentium4 pc we have at home. The system has a ralink wireless adapter(25xx something model) on the motherboard. The adapter is recognized.

Now I'm having trouble establishing a proper network connection via any wireless adapter. I tried following devices:


[INDENT]- Onboard chip which is mentioned above and normally supported by Ubuntu.

- Atheros based TP-Link PCI wireless adapter (TL-WN851N) which uses ath9k driver and functions perfectly on my brothers pc (xubuntu 11.10/ win7 dual boot).

-Dlink DWA 131 (USB) which also functions perfectly under Ubuntu 12.04 and Xubuntu 11.10 on the other pc.
[/INDENT]

The crazy thing is that i can perfectly connect to the internet by using these commands for the TP-Link card:

[COLOR="Blue"]- ifconfig wlan1 up
- iwconfig essid "networkname"
- dhclient wlan1
[/COLOR]

After using these 3 commands as superuser i get a perfect connection to the internet but the networkmanager still shows no connection and sais that all my devices are disabled by a hardware switch. So now I need to use these commands every time I reboot. And just putting this in a script is no solution because Software center doesn't work (It seems to rely on data from network manager).

Sidenote I already did:

[COLOR="blue"]- rfkill unblock all
- rfkill list all[/COLOR]

This shows that only the onboard wlan was disabled by hard- or software switch.

I also installed 12.04 but have yet to try it. It'll most likely be the same though. During the install I couldn't choose an acces point to connect to only a Wifi device to use.

I can supply more details from iw/ipconfig if need be.

I also installed windows driver with *ndiswrapper* now. It also recognizes the hardware but I don't know if or how I should use this driver.




All suggestions are welcome. Thanks in advance, Jors.


Edit: Just reading the sticky on ndiswrapper and some other thread gonna try some more with that tomorrow.

---

