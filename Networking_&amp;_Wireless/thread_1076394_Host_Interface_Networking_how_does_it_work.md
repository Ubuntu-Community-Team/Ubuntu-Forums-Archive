---
title: "Host Interface Networking: how does it work?"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by swiftarrow on 2009-02-21
Hi all,
I have been googling around for a way to set up my ubuntujeos lamp server in virtualbox, and to network it in such a way that I can access the server from the host's browser.
I've found many solutions, all variations of creating a bridge, etc.  I've tried them all (and a friend has too) but none have worked at all. What I want is:

My host should configure itself using dhcp via either eth0 and eth1
The guest can do whatever it wants re ip address
I want to access the guest's server from the host's browser, perhaps by typing in an ip address?
Also, when I'm in college, I dont have a network.  But I still want to access the guest server via host's browser.

As far as I can understand, I need to do the following:
1. Create a new network interface in the host, that will be connected whenever the guest is on (I guess).
2. Connect the guest to that interface in virtualbox.

I have dabbled in setting up a bridge with dhcp, setting up a tap, bridging all my interfaces, and connecting the guest, but the guest still seems not to know that it's connected to the network (although vbox says it is).

Another thread is here: [http://ubuntuforums.org/showthread.php?t=564353](http://ubuntuforums.org/showthread.php?t=564353)  Has there ever been a solution?

---

### Post by swiftarrow on 2009-02-22
ummmm..... bump?

---

