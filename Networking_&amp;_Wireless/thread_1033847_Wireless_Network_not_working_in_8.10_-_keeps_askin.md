---
title: "Wireless Network not working in 8.10 - keeps asking for password"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by tuxfan5 on 2009-01-07
I have Ubuntu 8.10.  Wireless was working perfectly in 8.04, but upgrading broke it.  Now, Ubuntu detects my network and attempts to connect.  However, it seems to keep timing out, and constantly asks for my ssid and password over and over again.  I have a gigabyte pci wireless card which uses the rt2500 driver.  I have tried troubleshoot after troubleshoot using ubuntu docs.  Everything I try says that its working perfectly.  I'll post the output to those commands at [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681), but I'm on my windows partition right now.  Any ideas?  I'm considering switching distros if I can't get this to work, but I'd prefer it be fixed than have to switch.  I'm running an x84 processer.  Any help would be appreciated.

---

### Post by dougpan on 2009-01-07
Just a long shot but you might want to check and see if you have IPV6 turned on.

If it is the problem might be with ipv6 waiting for ip activity too long. The same problem happens on Fedora 5 Linux with the atheros chipset. I found that turning on IPV6 makes the wait time shorter or something. Turning it off seemed to allow it to not time out.

The following explains how to turn off ipv6 by changing the setting in the file /etc/network/interfaces

iface eth0 inet dhcp

The above line means that interface (“iface”) eth0 should have an IPv4 address space (replace “inet” with “inet6” for an IPv6 device) and that it should get its configuration automatically from DHCP.

See: [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

Doug

---

### Post by tuxfan5 on 2009-01-07
Nope, that didn't work.  I forgot to mention that I am currently using the ndiswrapper windows driver, as I had previously tried to use the default one, and that didn't work.  I'm attaching the results of what I said I'd do before now.

---

