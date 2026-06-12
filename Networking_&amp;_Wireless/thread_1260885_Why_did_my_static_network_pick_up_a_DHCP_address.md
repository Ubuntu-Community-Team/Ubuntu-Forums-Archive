---
title: "Why did my static network pick up a DHCP address?"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by rexkerr on 2009-09-08
I installed Ubuntu Server (9.04) on my home server almost two weeks ago (Via A2000, as if it matters).  It has been running great w/o a single reboot ever since.  I've logged into it hundreds of times and have kept it quite busy getting my services set up and distributed on the hard drives.  Then this evening I couldn't log into it.  After a reboot (I don't have a USB keyboard handy to use it from the console, so I had to soft reboot w/ the power button) I was able to log in via SSH and started poking around the syslog to see what happened and I saw these messages were logged a few hours before I discovered the problem:

[INDENT][FONT=Courier New]Sep  7 19:32:52 a2000 dhclient: DHCPREQUEST of 192.168.1.105 on eth0 to 192.168.1.1 port 67
Sep  7 19:32:52 a2000 dhclient: DHCPNAK from 192.168.1.1
Sep  7 19:32:53 a2000 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Sep  7 19:32:54 a2000 dhclient: DHCPOFFER of 192.168.1.102 from 192.168.1.1
Sep  7 19:32:54 a2000 dhclient: DHCPREQUEST of 192.168.1.102 on eth0 to 255.255.255.255 port 67
Sep  7 19:32:54 a2000 dhclient: DHCPACK of 192.168.1.102 from 192.168.1.1
Sep  7 19:32:54 a2000 dhclient: bound to 192.168.1.102 -- renewal in 247581 seconds.
[/FONT][/INDENT]Strange... why did it get a dynamic address?  So I looked at my /etc/network/interfaces file and it appears to be configured correctly:

[INDENT]auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
   address 192.168.1.10
   netmask 255.255.255.0
   broadcast 192.168.1.255
   gateway 192.168.1.1
[/INDENT]Looks right... strange.

So... any idea why it picked up a dynamic IP?   I can't find anything in the neighboring lines that seems to be the culprit.

Ideas?

Thanks,
-Rex

---

### Post by rabinski on 2009-09-08
I have the same problem on my desktop. I have it assigned to 10.1.1.11 but it is using 10.1.1.136 which I assume is from DHCP

---

### Post by jamest09 on 2009-09-08
Is networkmanager running? Does that override the interfaces file?

---

### Post by rexkerr on 2009-09-08
> **jamest09 said:**
> Is networkmanager running? Does that override the interfaces file?

That crossed my mind, but I can't find any log entries indicating that network manager did anything.  My syslog is COMPLETELY empty except for the bootup sequence, many days worth of cron entries, the DHCP lines above, and then the shutdown sequence when I rebooted.

How would I determine if network manager is running?  pgrep nm and pgrep net don't return anything.  On my laptop, running Kubuntu 8.04 I've found that if I have settings in the interfaces file I can't override them w/ nm even if I want to, which is annoying in that I cannot connect to the wireless until after I've logged in, but if I put my home network configuration in the interfaces file I cannot manually select a wireless network while traveling.  That's a different issue though, my point was that in my past experience nm won't override the interfaces file.

---

### Post by Iowan on 2009-09-08
> **rexkerr said:**
> On my laptop, running Kubuntu 8.04 I've found that if I have settings in the interfaces file I can't override them w/ nm even if I want to... Jaunty is supposed to work that way, too. Network Manager is supposed to ignore an interface that is configured in */etc/network/interfaces*. (Not to mention that the default server install (CLI-only) doesn't use Network Manager. Desktop is a different story.)
You might try removing **dhclient**... or setting up DHCP server to assign the server the address you wanted it to have anyway (AKA static lease, or fixed address).

---

### Post by rexkerr on 2009-09-08
> **Iowan said:**
> Jaunty is supposed to work that way, too. Network Manager is supposed to ignore an interface that is configured in */etc/network/interfaces*. (Not to mention that the default server install (CLI-only) doesn't use Network Manager. Desktop is a different story.)
You might try removing **dhclient**... or setting up DHCP server to assign the server the address you wanted it to have anyway (AKA static lease, or fixed address).


Well that explain why I can't find any remnants of nm on the machine, being as it's Ubuntu server.  I wish I could configure my DHCP server to hand out the address, but that'd require an aftermarket firmware or a new device... perhaps eventually this computer will be the DHCP server, but I haven't gotten around to it.  I might consider trying to remove dhclient since I really don't need it.

Thanks.

---

### Post by Iowan on 2009-09-08
> **rexkerr said:**
> W perhaps eventually this computer will be the DHCP server, but I haven't gotten around to it. I just installed **dnsmasq** on a machine destined to replace my Breezy server.  **dnsmasq** is supposed to do DNS and/or DHCP - and tie the two together to ease using hostnames on a DHCP network.

---

