---
title: "Configure a LAN"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by artium on 2012-10-21
I have an ADSL Internet and I used to connect my computer directly to the ADSL modem. The configuration was done with pppoeconfig wizard and it worked almost perfectly.

Now I bought a wireless router. I connected the computer to the LAN port but Ubuntu does not recognize the local network at all. I tired to add a new connection through a "Network Connections" GUI, but all options are grayed out.
When I boot from windows, the network is recognized automatically, and I can surf the Internet without any configuration.

My guess is that the pppoe configuration is interfering, so y question is how can I remove it or reset the configuration to factory defaults? 
But even if I will be able to configure my network manually after that, there is stil a question of why Ubuntu does not recognize and configure automatically like Windows does? 

Thank you

---

### Post by artium on 2012-10-22
Here is how my /etc/network/interfaces file looks like (manual copy paste).

```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```Maybe someone will see something wrong here.

---

### Post by qubits4all on 2012-10-23
The configuration file you posted indicates that your primary Ethernet NIC is indeed misconfigured, given your new network setup. If your router has its default settings, i.e. you haven't made a bunch of changes, I would suggest changing your eth0 device to ask for its configuration from the router via DHCP, a simple change as follows. (This is the default setting for a new network card in Windows since at least XP, and is also the default used during the Ubuntu install process.)

Firstly comment out (or remove) the 4 lines starting with:

   auto dsl-provider

by inserting a # at the beginning of each line. These are remnants from when you were connecting directly to your DSL modem.
Then change your last line from:

   iface eth0 inet manual

to:

   iface eth0 inet dhcp

That should do the trick, by telling your network card to always get its IP address, default route (to the Internet) and DNS settings from your router.

---

