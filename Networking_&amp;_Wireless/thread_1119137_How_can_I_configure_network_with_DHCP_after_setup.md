---
title: "How can I configure network with DHCP after setup?"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by Mulenmar on 2009-04-07
It's a stupid question, probably, but I haven't seen a how-to on how to do it. I don't want to reinstall everything just to run something to configure the network (and thus internet) automatically.

---

### Post by coffeecat on 2009-04-07
How are you connecting? Normally DHCP is the default. In fact, if you've plugged an ethernet cable between your computer and your router, you'll find that the router has already assigned you a LAN IP address, and that you're connected to the internet.

---

### Post by Mulenmar on 2009-04-07
It's just a broadband connection. I know DHCP is the default, I guess what I need is the command to run the DHCP util manually??

---

### Post by Mulenmar on 2009-04-07
Bumping

There's no router, it's a wired broadband connection. Really don't know that much about it.

---

### Post by Rluby on 2009-05-19
I have the same problem.  I've upgraded to 9.04, and somehow dhcpcd is not getting started, and I can't start it myself.  I've tried apt-get install  and I get a message that the archive us.ubuntu .....   is wrong and the installation aborts.  I've tried adding sudo , with the same result.

There are various files with dhcpcd in the filename, but I'd like a little advice.

I'm hooked up to a router  that is working ok under windows,

Ifconfig  tells me that the internet address for eth0 is 0.0.0.0 -  which has to be wrong.

Any ideas, folks?



> **coffeecat said:**
> How are you connecting? Normally DHCP is the default. In fact, if you've plugged an ethernet cable between your computer and your router, you'll find that the router has already assigned you a LAN IP address, and that you're connected to the internet.

---

### Post by Iowan on 2009-05-19
From a terminal, you can try **dhclient eth0** (or whatever your interface is). **ifconfig -a** will let you know if you successfully got an address.  If DHCP times out and goes "sleeping" you might edit /etc/dhcp3/dhclient.conf as described [here]("http://ubuntuforums.org/showthread.php?t=1156441").

---

