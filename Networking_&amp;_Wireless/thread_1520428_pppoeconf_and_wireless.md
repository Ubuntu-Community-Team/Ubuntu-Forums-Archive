---
title: "pppoeconf and wireless"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by Jonny Two Shoes on 2010-06-29
Hi there,

As a Linux noob it took me 3 format re-installs of Ubuntu 10.04 32bit edition to get this far but still have not fixed the issue.

I am using a Dell Latitude D610.  I intend to use wi-fi but seeing as I have my own DSL account sharing one router with other people I need to use pppoeconf to dial into my own DSL account. (For some reason the network manager DSL tab does not work with wireless it only works with wired)

It seems every time I connect to wi-fi (which took me a while to figure out as the drivers were not working after clean install of Ubuntu and turns out I needed to update hardware drivers via wired ethernet which thankfully was detected as Broadcom B43 Wireless Driver) and then connect my DSL account using pppoeconf over the wireless then after the next reboot the network manager icon disappears at the top right of the screen.  What's more it seems all network is disabled after the reboot.

The best I can do is sudo restart network-manager which brings the icon back but everything is disabled.  nm-applet does nothing by the way I tried that to, just says it is already running.

I then figured out from another old thread here to delete etc/network/interfaces file using sudo rm then reboot the PC.  Then the icon is back and I can reconnect to the wi-fi and redo the pppoeconf for Internet.  But of course this just cycles the problem again and I am back to having no network manager after the next reboot.

Any ideas?

---

### Post by Jonny Two Shoes on 2010-06-29
Eish I just figured out I don't need to run pppoeconf again after reboot so it will no longer kill the network manager.  Sorry :)

Well to those with the same issue where pppoeconf kills your network manager simply do the following

1.  Open a terminal and type each line and press enter:
cd /
cd etc
cd network
sudo rm interfaces

2.  Reboot PC, your pppoeconf will still retain it's pppoe settings so you just need to type sudo pon dsl-provider the next time you want to connect.

Of course if you need to change anything in pppoeconf you will need to do this all over again and delete the interfaces file and reboot again etc...

---

