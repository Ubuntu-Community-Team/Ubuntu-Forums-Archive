---
title: "Two NICs. DHCP Server. Which NIC is handling it?"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by Roasted on 2011-04-19
I have two NICs in my interface file. One is to a 192.168.x.x network that I want to run DHCP3 Server and hand out IPs in a test environment with no outbound access. The other is simply set up to receive DHCP addresses. 

I'm trying to figure out which NIC is handling DHCP. I know which IP is set to which NIC but I don't want the wrong one to do the handouts. 

Any ideas?

---

### Post by SeijiSensei on 2011-04-19
Specify the interface you want dhcpd to use on its command line; e.g., "dhcpd eth1" will bind the server to eth1.  If you edit the file /etc/default/dhcp3-server, it will work correctly at boot.

---

### Post by Roasted on 2011-04-20
In my server I had:

INTERFACES=""

Listed in the defaults/dhcp3 file. If I add "eth1" to it, showing:

INTERFACES="eth1"

Would it bind DHCP to that interface accordingly?

---

### Post by SeijiSensei on 2011-04-20
Yes.  Just restart dhcp3-server.  If you run "ps ax | grep dhcp" you should see the eth1 on the command line.

To see how this works, look at /etc/init.d/dhcp3-server.  You'll see the line that starts the daemon with "$INTERFACES" at the end of it.

---

