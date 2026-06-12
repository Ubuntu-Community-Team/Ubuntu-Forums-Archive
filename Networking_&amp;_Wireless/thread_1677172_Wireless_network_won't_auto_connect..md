---
title: "Wireless network won't auto connect."
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2011-01-28
I've been trying to get and old PCI wireless card to work on Ubuntu 10.04. The card is a Zonet 1602. It was not recognized automatically.

I have been able to get it to work using ndiswrapper except that when the computer is started it does not automatically connect to the network. I can click on the network icon and select my network from a list and it will connect, including properly authenticating the network key.

I have worked through a lot of information on the web but much of it seems to apply to earlier versions of Ubuntu and some if it does not match what I'm seeing in 10.04.

There is a built in Ethernet controller on the mother board but I have disabled it in the BIOS.

Any pointers would be appreciated.

---

### Post by rsteinmetz70112 on 2011-01-28
Still not working. I tried looking for a setting that I can change in the auto profile that was created. No Luck, I can click the "Connect Automatically" check box but I can't save the profile. 

I created a wireless connection profile with all of the correct information Called "Wireless Profile 1", it has never connected and now I can't edit it either.

---

### Post by grahammechanical on 2011-01-28
Have you tried right clicking the network manager icon, selecting Edit connections, selecting the wireless connection (it should be called Wireless Profile 1), clicking Edit and ticking the box marked Connect Automatically?

Regards.

---

### Post by rsteinmetz70112 on 2011-01-29
I've tried clicking on every icon I can find that is network related. I don't see anything labled "Network Nanager" There is unnameed indicator on the top bar that lists detected wireless networks and I can select the right one from there. But there are no options to edit the settings.

UNder Systems->Administration the only two Network related Selections are "Network Tools" and "Windows Wireless Drivers".

Under Systems->Preferences there is a selection called "Network Connections"

If I select Systems->Administration->Windows Wireless Drivers and then select "Configure Netwrok" that brings up the "Network Connection" the same windows availible under Preferences.

In the "Network Connections" Window I have two wireless "Connections" One is labled "Wireless Connection 1" and has never been connected. I can edit and save that one but have no known way to access it. The othe Wireless Connection is labled "Auto <essid> " And I can connect using it and acccess its setting but can not make changes, the "Apply" button is greyed out.

---

