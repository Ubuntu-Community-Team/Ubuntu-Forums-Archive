---
title: "Home network problems (systems cant find each other)"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by AndyGibo on 2009-08-15
Hi again, I have another problem!!!!!

I have a home network made up of 3 ubuntu systems, 1 acting as a file/printer server.  The server is running 9.04, the other 2 are 8.10 and 8.04.  

My problem(s) are that they are having difficulty seeing each other.  I have manually edited the /etc/hosts file so that i can ping the systems by name.  However when i try to add the shared printer to the other 2 systems across the network, they are unable to see the server.  I have tried editing the /etc/resolv.conf file but everytime i restart the systems, any changes I have made are undone.

Please can someone offer advice, hints or tips to setting up a home network with ubuntu.  It has to be easier than this!!!

---

### Post by Iowan on 2009-08-15
Are the machines configured with static addresses, or is there a DHCP server?

---

### Post by AndyGibo on 2009-08-15
The systems are all set to DHCP.  IP Addresses are given out from router (crappy thing from Sky).

---

### Post by superprash2003 on 2009-08-15
well if they are set to DHCP , then ip addresses of the machines could change everytime , therefore the entries inserted in the /etc/hosts file could be useless..

---

### Post by Iowan on 2009-08-15
Depending on DHCP server (router), it might be possible to set up static leases - based on MAC address. DHCP seems to overwrite */etc/resolv.conf*, too, but the hosts file might work.

---

### Post by AndyGibo on 2009-08-15
IP Addresses are reserved by the router based on MAC address, so the /etc/hosts file is fine.  The /etc/resolv.conf always loses any changes I make after the system restarts.  

Is there anyway of checking that all the systems are in the same workgroup?  I have already checked the /etc/samba/smb.conf file.

---

### Post by AndyGibo on 2009-08-16
Bump Bump

---

### Post by AndyGibo on 2009-08-16
Bump again

---

### Post by Iowan on 2009-08-16
The Ubuntu systems use */etc/dhcp3/dhclient.conf*. That file has a "prepend" line that can be used to force your DNS server(s) of choice to the top of the list. This information *should* get written to */etc/resolv.conf*.

---

### Post by dbalascak on 2009-08-16
Do you have access to configure the router?  Most Internet providers do not let you see the Internet side but some allow you to configure the home LAN side. You may be able to make the DHCP range smaller thereby leaving some IPs to be used for hosts with static IP configurations.  For example if you were to set the  DHCP range to be 192.168.x.50 thru 254, the range .2 thru .49 could be used for static IPs on hosts.  This is assuming the .1 is used for the SKY router.

---

