---
title: "Netgear WG111 v1 Drivers and Setup?"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by VmKid95 on 2011-01-23
I've got a computer with a Netgear WG111 wireless dongle, however I don't have the setup CDs and I don't know how i'd get it working in 10.10 anyway.  Can someone point me in the direction of the drivers and a guide on how to install them?

---

### Post by Tedd81 on 2011-01-23
Hello!

I'm setting up a WG111t at the moment so have a little experience.

You will need the windows drivers, google for them.

Try following:

[https://help.ubuntu.com/community/WifiDocs/Device/WG111T]("https://help.ubuntu.com/community/WifiDocs/Device/WG111T")

I know its a T model not v1 but the idea is the same.

Or look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

or:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB")

good luck!

Ted

---

### Post by eltomate on 2011-02-28
Just set up my Netgear WG111 today, use 'sudo apt-get install linux-firmware-nonfree' in a terminal.  Do this while connected to the internet via some other means, and you should be able to get it rolling with the ndiswrapper games.

---

### Post by PCNetSpec on 2011-03-30
Don't use ndiswrapper, there are Linux native drivers for the Netgear WG111T.

Instructions here:
[http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572](http://linuxforums.org.uk/ubuntu/netgear-wg111t/msg29572/#msg29572)

---

