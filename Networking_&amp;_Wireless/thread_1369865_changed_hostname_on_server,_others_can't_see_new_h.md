---
title: "changed hostname on server, others can't see new hostname"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by talz13 on 2010-01-01
I just changed the hostname and IP of my server yesterday (from server2 to server) in the /etc/hostname and /etc/hosts file, and updated my router config (for the static DHCP settings) to reflect the new hostname.  However, all the rest of the PCs on the network still see it as "server2" at the new IP I gave it.  "server" is not found.  Is there something else I need to do here?

---

### Post by Iowan on 2010-01-01
If it's a Samba server, you may need to change the Netbios name in */etc/samba/smb.conf*
Does server have a static address - or does it get a static lease from router? If a static lease (meaning server still uses dhclient), you may need to change the "send host-name" line in */etc/dhcp3/dhclient.conf*

---

### Post by talz13 on 2010-01-01
It is set up as a static DHCP lease.  I just checked the /etc/dhcp3/dhclient.conf and it appears to be using "send host-name "<hostname>";".  If I run hostname on the server, it outputs "server" as it should.

Also, if I try to ping "server" from elsewhere on the network it just tells me that it "could not find host server. Please check the name and try again."



edit:  I found that the windows PCs and WDTV devices seem to have trouble finding the new hostname, but the other ubuntu PC I have can ping it without issue.

---

### Post by Iowan on 2010-01-01
What is acting as local DNS server? If it is the DHCP server, try changing "<hostname>" to "server" - and restart/reboot.

---

### Post by talz13 on 2010-01-02
My linksys router (running tomato) is the DHCP / DNS server.  The server PC is getting its IP from the router, and everything else on the network (besides the other ubuntu PC) still sees it as hostname "server2".

---

### Post by talz13 on 2010-01-06
Any other ideas?  I can get to my server as 'server' when I am tunneled in from another PC on the internet, so maybe something is missing with the rest of the computers on my local network?  Do they need to flush their DNS or something?

---

### Post by Iowan on 2010-01-06
Check the leases in the router/DHCP/DNS server - which name does it have?

---

