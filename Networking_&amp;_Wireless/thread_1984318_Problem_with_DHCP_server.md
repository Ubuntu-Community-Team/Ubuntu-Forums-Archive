---
title: "Problem with DHCP server"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by rockballad on 2012-05-21
Hello,

I've installed a DHCP Server on a machine (Laptop1, 192.168.0.15). But it looks unstable. Sometimes when a new machine (Laptop2, MAC addr is a2:aa:bb:e2:e2:3a) is booted, it can't request an IP. Other time it doesn't make a request at all. Here is the log:

**Case 1:** everything is OK
> May 20 15:01:03 Laptop1 dhcpd: DHCPDISCOVER from a2:aa:bb:e2:e2:3a via eth0
May 20 15:01:03 Laptop1 dhcpd: DHCPOFFER on 192.168.0.102 to a2:aa:bb:e2:e2:3a via eth0
May 20 15:01:03 Laptop1 dhcpd: Dynamic and static leases present for 192.168.0.102.
May 20 15:01:03 Laptop1 dhcpd: Remove host declaration pub02 or remove 192.168.0.102
May 20 15:01:03 Laptop1 dhcpd: from the dynamic address pool for 192.168.0/24
May 20 15:01:03 Laptop1 dhcpd: DHCPREQUEST for 192.168.0.102 (192.168.0.15) from a2:aa:bb:e2:e2:3a via eth0
May 20 15:01:03 Laptop1 dhcpd: DHCPACK on 192.168.0.102 to a2:aa:bb:e2:e2:3a via eth0

**Case 2:** Can't obtain an IP
> May 20 14:37:36 Laptop1 dhcpd: DHCPDISCOVER from a2:aa:bb:e2:e2:3a via eth0
May 20 14:37:36 Laptop1 dhcpd: DHCPOFFER on 192.168.0.102 to a2:aa:bb:e2:e2:3a via eth0
May 20 14:37:36 Laptop1 dhcpd: DHCPREQUEST for 192.168.0.12 (192.168.0.1) from a2:aa:bb:e2:e2:3a via eth0: lease 192.168.0.12 unavailable.
May 20 14:37:36 Laptop1 dhcpd: DHCPNAK on 192.168.0.12 to a2:aa:bb:e2:e2:3a via eth0


--> 192.168.0.1 is my router. Maybe it requests 192.168.0.12 for the Laptop2 but unsuccessfully. The Laptop2 has no networking after all.

**Case 3:** Laptop3 doesn't "notify" the DHCP server at all. There's no log on DHCP server, even though it uses "dhcp" mode.

Could you tell me what's wrong w/ this DHCP Server. I'm so confused.
Thank you very much.

---

### Post by sikander3786 on 2012-05-21
Are you sure the router's built-in DHCP server has been turned off, if it offers something like that?

And secondly, please post your dhcpd.conf files.

---

### Post by rockballad on 2012-05-21
Hello,

I can turn off the DHCP of the router at my home to test, but I can't do it at my company. 

Here is my dhcpd.conf

> 
#ddns-update-style	interim;
#ddns-updates		on;
#allow			client-updates;


include "/opt/data/dhcpd.entries";


# specify domain name
option domain-name "server1";

# specify DNS's hostname or IP address
#option domain-name-servers	dlp.server.world;

# default lease time
default-lease-time 600;

# max lease time
max-lease-time 7200;

# this DHCP server to be declared valid
authoritative;

# specify network address and subnet mask
subnet 192.168.0.0 netmask 255.255.255.0 {

	# specify the range of lease IP address
	range dynamic-bootp 192.168.0.200 192.168.0.254;

	# specify broadcast address
	option broadcast-address 192.168.0.255;

	# specify default gateway
	option routers 192.168.0.1;
}


/opt/data/dhcpd.entries
> 
host priv01 {
  hardware ethernet A2:AA:BB:1D:24:B3;
  fixed-address 172.20.6.10;
  option host-name "priv01";
  option subnet-mask 255.255.255.0;
  option routers 172.20.6.1;
  option broadcast-address 172.20.6.255;
  option domain-name-servers 192.168.0.1;
}
host priv02 {
  hardware ethernet A2:AA:BB:2C:83:10;
  fixed-address 172.20.6.11;
  option host-name "priv02";
  option subnet-mask 255.255.255.0;
  option routers 172.20.6.1;
  option broadcast-address 172.20.6.255;
  option domain-name-servers 192.168.0.1;
}
host pub02 {
  hardware ethernet A2:AA:BB:34:86:8B;
  fixed-address 192.168.0.202;
  option host-name "pub02";
  option routers 192.168.0.1;
  option domain-name-servers 192.168.0.1;
}



---

### Post by sikander3786 on 2012-05-22
I am not sure on how to configure two DHCP servers on the same network. Why would you want to keep running both of them even when there is only one router to be assigned?

Probably, there is a conflict between the two. You can wait for other ideas.

---

### Post by rockballad on 2012-05-22
> **sikander3786 said:**
> I am not sure on how to configure two DHCP servers on the same network. Why would you want to keep running both of them even when there is only one router to be assigned?

Probably, there is a conflict between the two. You can wait for other ideas.

I see. I'll disable the one on router. Thank you a lot!

---

