---
title: "Wirelessly connect from a terminal?"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by dillandriskell on 2010-06-04
Right now I'm not using a GUI, just a terminal, and I won't be using a GUI for
a little while (long story lol). Anyways, I'm trying to connect to the
internet from my laptop using a terminal. I've found plenty of guides on this,
but none have worked for me.

I have the WEP key, the SSID, pretty much everything. Here are the commands
I was told to enter into the command line;

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "Didesch"
sudo iwconfig wlan0 key <my key>
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

And upon doing that it goes through like 6 port 67 intervals before saying:

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Absolute beginner talk please, any help would be very much appreciated.

---

### Post by dillandriskell on 2010-06-04
bump

---

