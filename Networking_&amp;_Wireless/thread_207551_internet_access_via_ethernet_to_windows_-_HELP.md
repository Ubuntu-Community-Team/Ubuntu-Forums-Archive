---
title: "internet access via ethernet to windows - HELP"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by jrleighton on 2006-07-02
I have a wireless router with broadband access.  My windows XP PC is connected to the router via a wireless connection.  My kubuntu dapper PC is next to the windows PC (but both are physically some distance from the router - hence the wireless and not wired approach ) and I want to get kubuntu internet access using the windows PC as a middle-man.

I have tried many things, but not come close to succeeding. Does anyone know how this should work ?

I have tried a windows network bridge between the windows PC LAN connection and the wifi connection - but that gets into IP address conflicts.
I have tried windows internet connection sharing (without the network bridge and with it) on my wifi connection, but the kubuntu PC isn't getting connected to the windows PC that way.

I would like (of course) to connect my kubuntu via wifi directly to the router, but that's not a winner either as I am having severe difficulties with both my usb adapters (rt73 and rt2500 chipsets - tried native linux drivers and ndiswrapper - no-go), so hence I want to go for the wired connection via windows.

Thanks in advance for any help out there.

---

### Post by mips on 2006-07-02
Enable internet connection sharing on Win. Note the second network adapter MUST be configured with totally different network settings.

Set up Kubuntu for DHCP. If it does not work use static ip address settings that are in the same network as the shared adapter on win but the address cannot be the same.

---

