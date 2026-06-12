---
title: "Problem configuring network connections"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by MakubeX on 2011-01-06
Hi! I have a problem configuring my network connection. My lab setup includes having a static IP address. There was no prompt for network configuration during the installation of Ubuntu 10.10 (via Wubi - WindowsXP) so the network was not yet set.

Then I configured the network interface by setting all the values (IP, subnet, gateway, DNS, etc.) and the connection worked. However, after a shutdown/reboot, it doesn't connect anymore. I checked the list of network interfaces and now there's another interface that was created from nowhere (e.g. there was eth0 before, not it has eth0 and eth1). Sometimes, the MAC Address that was set on one interface does not match the MAC address when i do a /sbin/ifconfig command.

This situation happened to me way back in Ubuntu 10.04 as well.

Also, when I do a /sbin/ifconfig command, only "lo" was present and no eth0/eth1 was shown on my Terminal.

It becomes tedious because I have to reconfigure all the time only to find out that my settings were not permanent at all.

I need help. :)

---

### Post by JeffDavidoff on 2011-01-06
So that the configuration remains after reboots you have to save the configuration in the configuration files. 

Heres' how to use the command line: [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

Here's how to use the graphical tool: [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

---

### Post by MakubeX on 2011-01-06
Thanks for the suggestions. 

I'll try that command line method later. I inspected a working machine and I was wondering why it doesn't seem to follow what was shown on the command line howto. The machine was set to static IP but there was nothing about it that was found at the /etc/network/interfaces file. And thing is, it works!

About the graphical method - I know how to set it but it still did not work. (the howto's old as well by the way)

---

