---
title: "Unable to get wireless networking connected"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by phil7784 on 2009-04-14
I am new to Linux and am trying to use Ubuntu 8.10 on my new Eee PC 1000HA. Installation went fine but I cannot figure out how to connect to my home wireless network. The netbook came with Windows XP installed and I had no trouble configuring it to work perfectly with the network. Booting the netbook offers me the option to boot to Ubuntu or to XP.  Hardware consists of a D-Link DCM-202 cable modem (Comcast) and a Belkin wireless  54G router (model F5D7230-4). The netbook also works perfectly using Ubuntu to access the internet with an ethernet cable connected to the router. I have tried the forum looking for the right thread, but so far have not been able to find anything that addresses my problem.
Specifically, booting into Ubuntu I tried all the tutorials, but they do not help. The notification area shows 2 overlapped computer screens and says "no network connection". Enable networking is selected; edit connections goes to a dialog box labelled network connections with several tabs. Under the wireless tab nothing is listed. Shouldn't there be a list of available networks? There is an add (+) button which brings up another dialog asking for SSID; mode; BSSID; MAC address. I have no idea what to do with these. In XP connecting was simple - the network dialog shows available networks and then I simply had to put in the wireless security key, which in this case consists of 5 two digit hexadecimal numbers.
Ubuntu looks and feels fine, but is useless to me if I can't connect to my or any other network. Can anyone help?

---

### Post by bestxhack85 on 2009-04-14
hi, try to enable your restricted driver for the wireless network adapter at  : system> administration> hardware drivers.

---

### Post by RedSingularity on 2009-04-14
Post the output of "lspci" in the terminal.

---

