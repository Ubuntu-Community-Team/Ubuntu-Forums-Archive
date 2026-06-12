---
title: "Static IP trouble"
date: 2010-02-12
forum: Networking &amp; Wireless
---

### Post by bej006 on 2010-02-12
I want to use a static ip address on my wireless network but when I click configure in network tools it keeps telling me The interface does not exist and to Check that it is correctly typed and that it is correctly supported by your system. If anyone could help I would greatly appreciate it.

---

### Post by arvevans on 2010-02-12
Network Tools are those tools you use in conjunction with network connections to do things via the network.  This is not the place where you set your IP address.

Go to System|Preferences|Network Connections

This is where you can set your fixed or dynamic IP address selection, and the actual IP numbers if you choose fixed.

I know this is a strange place for setting your IP address (seems it should be in "Administration") but this is where 'they' put it, so you have to go there.

---

### Post by bej006 on 2010-02-16
There doesn't seem to be network connections in preferences or anywhere for that matter. There is only 'network' and 'network tools' in administration.

---

### Post by efflandt on 2010-02-16
Are you running regular Ubuntu (9.10?) or some other variation?  Or did you install some other wireless network tool that conflicted with and removed the **network-manager** package?

Or maybe you need a driver for your wireless (is it Broadcom?).  Does **sudo iwlist scan** show any access point(s)?

If you set static IP, netmask, you also need to set gateway (LAN IP of your router) and nameserver(s) (often the LAN IP of your router if it handles/caches DNS).

---

### Post by lisati on 2010-02-16
My $0.02: I prefer to set static IP's in my router. I do this by associating a specific IP address with a specific MAC address.

---

### Post by Iowan on 2010-02-16
My Karmic machine has System>Preferences>Network Connections, this Hardy machine does not. Which version are you running?

(For what it's worth - I also like static leases)

---

