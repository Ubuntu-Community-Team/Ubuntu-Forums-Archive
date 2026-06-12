---
title: "Sun Quad FastEthernet Card with Ubuntu 10.04 Server"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by FlameLicker on 2011-01-18
Dear all,

I bought a Sun Quad FastEthernet PCI Card and put it into my Ubuntu 10.04 32bit server. Large and by the card works. 

Unfortunately the card changes the MAC addresses randomly on every reboot. Thus the udev network rules grew further and further and the port number increased by 4 on restart.

As a countermeasure I delete the udev rules on reboot so that there are only 4 entries and set the MAC addresses in the interfaces file.

Supposingly the change of MAC addresses still happens in the beginning of the card initialization and influence the order of the port names. That means that the physical port changes the configuration on reboot.

I tried to decipher the source code of the card driver sunhme to figure out if there is any opportunity to set the MAC address in the code but I'm not a programmer and I couldn't find anything what made sense to me.

Is there any smart solution or do I need to think about a workaround like probing the possible networks on each port after reboot and adjusting the interfaces file afterwards?

Any help will be taken gratefully. Thanks in advance.

---

