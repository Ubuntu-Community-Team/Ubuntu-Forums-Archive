---
title: "Trying to set up dhcp server"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by jmmL on 2010-01-19
I'm trying to get a dhcp server running on my laptop. I want devices to be able to connect to a wireless AP I've set up (using hostapd) to then connect to the rest of the internet via my ethernet connection from the laptop.

However, I can't get dhcp to work properly. It always fails, leaving this message in the syslog```
Jan 19 15:49:15 lucid-laptop dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Jan 19 15:49:15 lucid-laptop dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Jan 19 15:49:15 lucid-laptop dhcpd: Wrote 0 deleted host decls to leases file.
Jan 19 15:49:15 lucid-laptop dhcpd: Wrote 0 new dynamic host decls to leases file.
Jan 19 15:49:15 lucid-laptop dhcpd: Wrote 0 leases to leases file.
Jan 19 15:49:15 lucid-laptop dhcpd: 
Jan 19 15:49:15 lucid-laptop dhcpd: No subnet declaration for wlan1 (0.0.0.0).
Jan 19 15:49:15 lucid-laptop dhcpd: ** Ignoring requests on wlan1.  If this is not what
Jan 19 15:49:15 lucid-laptop dhcpd:    you want, please write a subnet declaration
Jan 19 15:49:15 lucid-laptop dhcpd:    in your dhcpd.conf file for the network segment
Jan 19 15:49:15 lucid-laptop dhcpd:    to which interface wlan1 is attached. **
Jan 19 15:49:15 lucid-laptop dhcpd: 
Jan 19 15:49:15 lucid-laptop dhcpd: 
Jan 19 15:49:15 lucid-laptop dhcpd: Not configured to listen on any interfaces!
```Here's my /etc/default/dhcp3-server```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="wlan1"
```and here's dhcpd.conf```
# /etc/dhcpd.conf
# Deny all unknown clients and do not try to be authoritative
# source of DHCP information by default 
deny bootp;
#deny unknown-clients;
not authoritative;
use-host-decl-names on;

# Your ISP's name servers go here
option domain-name-servers <removed>;

# Your ISP's domain name
option domain-name "<removed>";

# The local address and subnet mask of this accesspoint
option routers 0.0.0.0;
option subnet-mask 255.255.255.0;

# How long before clients have to re-request their IP-address
# information.
default-lease-time 86400;
max-lease-time 86400;

# There has to be a subnet declaration for each interface in
# your computer. Otherwise dhcpd will bail at startup.

# This is the wlan1 subnet declaration
subnet 0.0.0.0 netmask 255.255.255.0 {
    # You can either define a range of addresses that are
    # given to connecting clients, or define static IP-
    # addresses for each client based on their NIC's
    # hardware address. You can also combine the two
    # approaches if you like.
    #
    # Hand out addresses from this pool    
    #range 0.0.0.1 0.0.0.5;

    # Define a static IP for a specific client
    host your_first_client {
        hardware ethernet 00:25:68:D1:18:22;
        fixed-address 0.0.0.1;
    }

}
```Can anyone tell me why it's failing?

---

### Post by Iowan on 2010-01-19
"wlan1" will need to have an address in the subnet (but outside the lease range. There are three private address ranges:
10.0.0.0 &#8211; 10.255.255.255
172.16.0.0 &#8211; 172.31.255.255
192.168.0.0 &#8211; 192.168.255.255
You should probably use one of them.
The router address should be the next machine upstream - your router or your ISP's.

---

### Post by jmmL on 2010-01-20
Okay, thanks that part now works. Now my device is assigned an IP address.
However I still can't access the internet from my device. I tried using internet connection sharing with firestarter, but it doesn't seem to work. What logs should I post to help diagnose? Also, how can I determine whether DNS is working for my device - I put the DNS server address of my university in hostapd.conf, but I guess my device can't see it yet as the connection between eth0 and wlan1 isn't shared.

Edit: I'm actually trying to connect with an android phone - the T-Mobile Pulse (also know as the Huawei U8220 or U8230).
Here's what the application Wifi Analyzer tells me about the network the phone is connected to:

IP address: 192.168.1.1
Lease duration: 86400 sec(24 hr)
Gateway: <redacted>
Netmask: 255.255.255.0
DNS1: <redacted>
DNS2: <redacted>
Server IP: 192.168.1.0
Link speed: 54 Mbps
Hidden SSID: No
Local MAC: 00.25.68.D1.18.22

I'm very novice at all this networking business. I've set my gateway using "option routers" in dhcpd.conf to the "default route" listed when I view the connection information for my wired connection.

I think that firestarter isn't sharing my connection properly, but I don't know how to fix this.

---

