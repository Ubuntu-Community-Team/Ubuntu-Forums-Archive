---
title: "Wired connection not working with Karmic Koala 9.10"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by surja on 2009-11-08
I have installed Ubuntu 9.10 on my desktop which has the following configuration.

Intel Core 2 Duo E4400 2 GHz
Biostar GF7050V-M7 motherboard (Motherboard Chipset	nForce7050-610i)
2 GB RAM
nVIDIA MCP73 - LAN Controller (PHY: Realtek RTL8201CL/CP) inbuilt LAN card
Realtek RTL8139 PCI Fast Ethernet Adapter [A/B/C] add-on LAN card.
I use an ADSL modem to connect to the internet. (A PPPOE type connection requiring an username and password to log in)

When I installed Ubuntu 9.10, Network Manager detected the 2 LAN cards and I used the pppoeconf tool to configure my internet connection and connect to the internet.
This worked for a couple of days. Then one day i start my computer and Network Manager showed that both cards to be inactive and it was written "device not managed" underneath the names of the two cards when i left clicked Network manager. I configured my connection again using pppoeconf and installed Wicd from the repos. This worked for a couple of days and now when my computer starts, a message box comes up saying wicd can't access the network cards and the wicd daemon could not start.

I havent had problems with ubuntu 8.10 or 9.04 but this release is not really working smoothly because I had problems with the graphics too. What a letdown.

---

### Post by chessmani on 2009-11-10
I read this somewhere, might be worth a try...

Check if you've got eth0 configured in /etc/network/interfaces. If so, remove or comment the entries.

---

