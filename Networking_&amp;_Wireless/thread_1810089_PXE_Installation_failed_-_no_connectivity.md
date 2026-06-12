---
title: "PXE Installation failed - no connectivity"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by SeaKing on 2011-07-22
I've tried to set up an easy PXE server to set up ubuntu on various PC's via network. I've used the [help article]("https://help.ubuntu.com/community/PXEInstallServer"). When I was finished I tried to boot a virtual mashine and later a normal notebook, both had the same problems, they find the TFTP server start booting and installing but it always fail. Reason: they get no IP from the DHCP-Server (I'm using dhcp3-server), even if I enter an IP manually I only get to the mirrow step where it tells me bad mirrow and the dhcp log says: Abandoning IP address 192.168.1.46: declined. I also rebootet the router but nothing changed. Where is the problem?

---

### Post by Dangertux on 2011-07-22
Is the dhcp server providing both the gateway and dns server information. 

PXE installs will not begin without the machine receiving an IP however without a gateway there will be no internet access available and without a dns server name resolution will not be possible. All of this can bs added to your dhcpd configuration.

---

### Post by SeaKing on 2011-07-22
Well everthing is configured in the dhcp-conf and I use bind9 as a cash only forwarding DNS Server. TFTP is configered to boot netboot and download all files from the internet.

Static address changes nothing.

---

### Post by SeaKing on 2011-07-23
syslog give me this DHCP "error":

DHCPDECLINE of 192.168.1.37 from <mac pxe client> via br0: abandoned

and the internet says:
ABANDONED - leases are never allocated for use - except as a last resort (there are no FREE leases remaining)but that's impossible, I have at least 45 leases/IP not in use

/E: Bios output: IP address seems to be 192.168.1.18/.192.168.1.13/192.168.1.1 (IP Address Client/TFTP-Server/DHCP-Router)

---

