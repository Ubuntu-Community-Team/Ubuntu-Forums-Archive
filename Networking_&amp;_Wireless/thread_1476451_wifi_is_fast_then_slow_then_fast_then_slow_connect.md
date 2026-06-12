---
title: "wifi is fast then slow then fast then slow connect disconnect ?"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by marcoftheknight on 2010-05-07
Hi peoples, THIS HAS BEEN SOLVED BY ME :) CHECK BELOW

My wireless seems to be fast for a good 30secs then bang takes good while to load the next page almost as if it's disconnecting and then reconnecting/scanning reconnecting. Why cant it stay connected. 

I have WAP PSK security here is my network setting please let me know if I should change any of them:
(side not is there a way to fix this problem occuring so frequently it says on the wiki that it should only occur once in a whilce 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

### Post by marcoftheknight on 2010-05-11
The resolution to this problem is to set a static IP WAHOOOOOOOOOOOO there is only one 
NOTE its not perfect but it does work better then the alternative still have to wait a few seconds every when it scannes and reconnects.

This is with the athros 9 chipset /driver 
I used wireshark to dignose the problem and used google search for the problem showing
I USE WCID (connection manager) FOR MY Connetion on ubuntu I also have WPA PSK security with no broadcast.

WAHOOOO!!! if you need anyhelp PM and I can probably guide you through

To set the static IP go to application>internet>wCID> click the network your connected to preferences click IP

you should know your router IP so assign an address add a 97 or a 2 at the end of the router address or something then paste that into the IP the subnet mask is usual
255.255.255.0 
gateway is your router IP
to find your DNS info
Type into the terminal to find these # cat /etc/resolv.conf 

DNS Domain : no-domain-set...
Search Domain: no-domain-set...
DNS 1: ROUTER IP goes here ) (ex: 192.168...)

Yah another one for the ubuntu

---

### Post by DannyBee on 2010-07-22
I am a newbie (3 months but new to the wonderful world of comps). I am sure the previous post is really good. I also am sure I don't know how even to start fixing this. Can I get a step-by-step?

---

