---
title: "Manual Wireless Interface Configuration"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by robinlmorris on 2011-03-30
Hi, 
  I am trying to manually configure my wireless interface similar to how I manually configure my wired interfaces on Ubuntu 10.10 (Maverick Meerkat).  I have two wired interfaces that use static IP addresses.  I set up these interfaces using /etc/network/interface file.  I disabled network manager (it was never working correctly to start with).
  Now,  I want to connect my wireless interface (wlan0) to an unsecured wireless private network.  I know/can find out all the information about the wireless network (ssid, etc).  Also, I need to do this without disconnecting either of my wired interfaces.  
   
  I have looked all over the internet/forums for information about how to set up this interface, but nothing I found meets my need.  Is there any way I can use iwconfig or the interface file to connect to this wireless connection?  Or is there any other tool that will allow me to manually do this?
                                         
   
  Thanks in Advance
  Robin

---

### Post by dmizer on 2011-03-30
Did you see this? [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

As to /etc/network/interfaces, here's an example entry for an unsecured access point:
```
iface wlan0 inet dhcp
wireless-essid XXXXXXXXXXX
```

You can find some good examples in /usr/share/doc/ifupdown/examples/network-interfaces.gz
More good manual information here: /usr/share/doc/wireless-tools/README.Debian

This may also be informative: [http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_network_configuration_with_ifupdown_legacy](http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_network_configuration_with_ifupdown_legacy)

---

### Post by robinlmorris on 2011-03-31
I had tried that already, and it didn't work (even after doing a bunch of iwconfig and ifconfig commands); however, I tried it again with "auto wlan0" above the "iface wlan0 inet dhcp" line , and it worked... should have tried that earlier :).

Thanks for links; they are helpful.

---

### Post by dmizer on 2011-04-01
> **robinlmorris said:**
> even after doing a bunch of iwconfig and ifconfig commands

Have you uninstalled network-manager? The network-manager tool and the ifconfig commands interfere with each other unless the interface is set to auto in the interfaces file.

If you're going to be handling your network configuration via command line, you'll be much better off uninstalling network-manager anyway.

Glad to have helped! :)

---

