---
title: "Network configuraton settings Issue"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by shaina2231 on 2010-06-24
i am tryint to set network configuraton in Ubuntu using following instructons

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

But the issue is that after making changes in /etc/network/interfaces file i m unable to save it. It ask for Save as but not save or append changes in original file

Plz help  how to sortout it
:confused:

---

### Post by byStanderone on 2010-06-24
...you can use the network manager to configure your network, but of course it is your choice if you really want doing it thru command line.

---

### Post by Iowan on 2010-06-24
> **shaina2231 said:**
> But the issue is that after making changes in /etc/network/interfaces file i m unable to save it. It ask for Save as but not save or append changes in original file
Which editor are you using to change the file? You could use **sudo nano /etc/network/interfaces** or **gksudo gedit /etc/network/interfaces**... dunno which version **vi** might need.

Some threads suggest that Network Manager must be removed for */etc/network/interfaces* to work properly.

---

