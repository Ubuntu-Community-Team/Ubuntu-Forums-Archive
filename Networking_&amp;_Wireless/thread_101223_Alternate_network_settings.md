---
title: "Alternate network settings?"
date: 2005-12-09
forum: Networking &amp; Wireless
---

### Post by GeirG on 2005-12-09
Hi,

In WinXP there is an 'Alternate Configuration' tab in the IP properties view.
This is pretty handy if you alternate between two networks and don't want to manually switch settings each time (i.e. fixed address at home, and DHCP at work).

Is there an 'Alternate Networkmanager' or a clever configuration of /etc/network/interfaces that would let me do this?

Regards

---

### Post by cwaldbieser on 2005-12-09
[QUOTE=GeirG]Hi,

In WinXP there is an 'Alternate Configuration' tab in the IP properties view.
This is pretty handy if you alternate between two networks and don't want to manually switch settings each time (i.e. fixed address at home, and DHCP at work).

Is there an 'Alternate Networkmanager' or a clever configuration of /etc/network/interfaces that would let me do this?

Regards[/QUOTE]

Not sure about a configuration that would do it, but you could just create youself a couple shell scripts that would do the switch.  Something like:
```

----- work-network.sh -----
#!/bin/bash

gksudo "ifdown eth0"
gksudo "dhclient eth0"
sudo -k
-------------------------------

----- home-network.sh -----
#!/bin/bash

gksudo "ifdown eth0"
gksudo "ifconfig eth0 192.168.0.2"
gksudo "route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1"
--------------------------------

```
You could add desktop shortcuts to them so you could just click them.

---

### Post by Lambert on 2005-12-09
Have you looked at gtkwifi or network manager? 

You can set up your interface though so it's something like this.

iface work inet dhcp


iface home inet static
xxx
xxx
xxx

fill in all the other detail needed and then to bring up an interface it would look something like this from a terminal.

sudo ifup wlan0=home

---

### Post by GeirG on 2005-12-09
Cwaldbieser: Yep, that was my first though too. But using the standard nework setup gui isn't that much work anyway, so I was kida looking for a fully automatic solution. Thanks for the example :-)

Lambert: Isn't GtkWiFi only for wireless?
I just found a reference to NetworkManager. Looks promising, I'll check it out.
Thanks for the suggestions.


Regards

---

