---
title: "How can I force a connection with iwconfig that network manager won't connect to?"
date: 2012-02-23
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2012-02-23
I need basic wireless (wlan0) connection & debugging advice & hints.

I'm at a friend's house who has a netgear home broadband router which will sometimes allow me to connect, and sometimes inexplicably drops the connection, and other times just won't connect (even though there are four bars showing in network manager & I can move the laptop anywhere near the router I want).

Sometimes it just won't associate; other times it will associate fine (four bars) in network manager - yet it won't be on the net (the router is set up as a DHCP server). Other times it works fine, yet, at some point, it just drops the connection.

The only thing I know it's not is signal strength, which is shows in airmon-ng (see below) at a good strength.

The 'only' thing that works, is I keep trying the following, and, eventually, (if I'm lucky), I'm connected:

[LIST]
[*]Reboot the router chain (cable modem, netgear router)
[*]Reboot the laptop\
[*]Kill the wireless connection & restart
[*]Delete the wireless connection & retype (surprisingly, this sometimes works)
[*]What else can I do?
[/LIST]
Googling, I've tried the following to debug:

[LIST=1]
[*]ifconfig (and then I look for the wlan0 IP address to see if DHCP worked)
[LIST]
[*]ifconfig wlan0
[/LIST]
 
[*]nm-tool (which tells me I'm 'connected' with a strength of "87" WEP
[LIST]
[*]nm-tool
[/LIST]
 
[*]airmon-ng (tells me it's channel 6 at 54MB WEP & -50 strength)
[LIST]
[*]sudo airmon-ng stop wlan0;sudo airmon-ng start wlan0;sudo airmon-ng; sudo airodump-ng mon0
[/LIST]
 
[*]etc.
[/LIST]
I need advice please.


I either need a better way to connect (and stay connected); or I need debugging commands to figure out why it's not connecting or dropping the existing connection.

---

### Post by rocksockdoc on 2012-02-23
I did try to connect without "network manager" by using iwconfig, but it didn't connect even though I know all the settings:

$ sudo iwconfig wlan0 essid NETGEAR channel 6 ap DE:AD:BE:EF:CA:FE key 12345678901234567890123456

BTW, if the 'key' is 26 characters, is the Network Manager choice supposed to be:

[LIST]
[*]WEP 40/128-bit Key
[*]WEP 128-bit Passphrase
[*]Dynamic WEP (802.1x)
[/LIST]
I'm using the first setting (because I'm not sure 'what' it is supposed to be).


PS: I'm using another laptop which 'is' on the network, without problems (Windoze though).

---

