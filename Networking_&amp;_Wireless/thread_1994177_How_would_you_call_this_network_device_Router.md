---
title: "How would you call this network device? Router?"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by jesushero on 2012-06-02
I'm having some weird network hardware incompatibility problems that I still haven't found a solution to. 

So, I need a device, which would take an ethernet internet connection (wired) from an ADSL modem, and would distribute this to a bunch of computers over wired ethernet, but not like a switch would. 

I want it to kind of split the network, so this device itself would have its own IP address and the computers taking their internet connection through this device would only communicate directly with this device, and NOT with the ADSL modem before it. I want the ADSL modem to kind of be invisible to the computers connected after this device.

I could do that with a purpose-built computer, with two ethernet adapters, and NAT. One ethernet adapter would be eth0, receiving an internet connection. The machine would have its own IP address, and would then provide DHCP and internet to the computers connected to the other ethernet adapter, which would be eth1 or so.. Then I would need a network switch between eth1 and the rest of the computers.

But is there something out there that already does all that, in one box? I really don't have a spare computer to use for that, nor enough time to set it all up from scratch.. 

Would a router do this?

A network switch doesn't. It experiences the same problems as the rest of the computers. LEDs flashing on and off repeatedly with no connection being made, due to the Ethernet carrier going on and off repeatedly.

The problem is that most of my computers will not recognize an ethernet connection to the ADSL router. Only one of them does, and at the moment this one is sharing the internet through wifi to the only other computer that supports wifi. So only two of the several computers actually have internet at the moment, and this setup is far less than ideal.

---

### Post by TVTrukChik on 2012-06-02
It sounds like a router is exactly what you want.  With a switch, you have multiple machines fighting for the single IP address your ISP has assigned to you, which is probably why you're having issues.  

The router would have an "external" IP address assigned via the ADSL modem by your ISP, and and "internal" IP address something like 192.168.1.1.  The router can then assign IP addresses via DHCP to your computers, which would get addresses in the 192.168.1.x range.

Get a router that has a built-in web browser, and use that to configure it.  The configuration disk that comes with it probably only works with Windows, but that shouldn't stop you if it has a built-in web interface.  You will probably have to dig into the documentation to find out the thing's default IP address.

---

