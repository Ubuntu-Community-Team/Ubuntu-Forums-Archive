---
title: "passphrase needed after every reboot - Why?"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by dgs2001 on 2009-03-29
Hi All 

Having finally got my wifi ubuntu laptop talking to the Internet :P

I would like to know how to make the connection automatic.

Everytime I reboot the machine I am asked to input the WPA Passphrase and a new instance of my SSID appears in network manager?

Is this normal?


Duncan

---

### Post by harbdog on 2009-04-02
I'm having the same trouble, every time I reboot the network manager completely forgets the previously entered wireless settings, be they auto or manually entered using DHCP.  This is with NetworkManager v0.7 in 8.10.  Its been happening only for the past few weeks or so, must have been an update in the last month which started it all.

---

### Post by freonchill on 2009-04-03
see this

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/36651](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/36651)

make sure that you have all updates done

then delete the entry and redo it, if that doesnt fix it,
you might have to add "purposed" to your update sources. and try again

either way, its a bug in network manager...

---

