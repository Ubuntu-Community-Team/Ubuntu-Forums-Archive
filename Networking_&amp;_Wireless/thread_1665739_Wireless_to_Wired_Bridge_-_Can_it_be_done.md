---
title: "Wireless to Wired Bridge - Can it be done?"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by Maddog Battie on 2011-01-12
Hi All,

I am trying to connect up a network as shown below:
[IMG]http://farm6.static.flickr.com/5090/5349868627_71bbc8827e_z.jpg[/IMG]

The NAS box has some windows shares on it and I would like this to be available to wireless side of the network.

The ideal solution would be to set up a network bridge between the wireless and wired interfaces in the Ubuntu box. The obvious software is bridge-utils but unfortunately, this doesn't work with wireless interfaces.

I've tried the "shared to other computers" graphical method but this sets up a NAT'ed network on the wired side which means that although connections can be made from the wired to wireless networks, connections don't seem to be able to be made in the other direction. This means that the laptop can't see the shares on the NAT drive.

Any pointers in the right direction would be gratefully received.

Cheers, MdB

---

### Post by Maddog Battie on 2011-01-13
If I plug the NAS box into the ADSL router then it all works as you would expect however I don't want to do this as the wireless link is slow.

I have also plugged a laptop into the eth0 port of the ubuntu box to show that the "shared to other computers" link works ok, which it does.

Is it possible to do something with iptables or the like (which I don't pretend to know) to get this working?

---

### Post by itspirit on 2012-02-01
I've got the same network and still didn't find any working solution. It is so simple to set bridge in windows, and I couldn't imagine that it is such an issue in ubuntu.

---

### Post by Nattereri on 2012-02-17
I don't know if this would work for your configuration but it works for bridging a LAN with wireless and virtual guest. I use **parprouted** and **bcrelay** to 'bridge' the wlan interface with the br0 interface and can connect to everything.
 
I have a network consisting of a windows box -> gigabit switch -> Ubuntu 10.04 box -> wlan interface -> wireless access point -> internet, with virtual guest running on the Ubuntu box. The DHCP is served from the wireless access point to the entire network and so far is working. I haven't tested the virtual guest yet but I will soon. Some old details of a previous configuration can be found in this thread [http://ubuntuforums.org/showthread.php?t=1766674](http://ubuntuforums.org/showthread.php?t=1766674).
 
Hope this works for someone.

---

