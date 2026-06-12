---
title: "Nvidia 6150 SE Integrated Ethernet and Jumbo Frames?"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by JohnnyPuffs on 2011-06-06
Hi All,

Running 11.04 on an Emachines Athlon II x 2 box..

[http://www.emachines.com/products/products.html?prod=EL1352-07e](http://www.emachines.com/products/products.html?prod=EL1352-07e)

It has the Nvidia GEforce 6150 SE in it. I can't seem to get Jumbo frames working on the Nic.

I have tried via the Network Connections Gui as well as the command line:

```
# ifconfig eth0 mtu 9000
```

It appears that forcedeth is being used.

I'm fairly new to using any kin of Linux Desktop.. Totally new to Ubuntu. I've mainly worked with Linux servers (headless) so didn't need to worry much about drivers, etc.

How can I get Jumbo frames working with this NIC? Do I need to install a proprietary driver? If so, where can I obtain this and how can it be installed?

Sorry for the newbish question!

Thanks in advance for any help anyone can provide.

Best,
JP

---

