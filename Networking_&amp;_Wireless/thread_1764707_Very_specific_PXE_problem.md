---
title: "Very specific PXE problem"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by Guerreiro on 2011-05-22
Hey all of you,

I have a Lenovo C-400 here that I need to boot into a PXE so I can rename the SAM file so my friend has her laptop back. I have one laptop I want the PXE server to be, but my laptop only has one Ethernet port, so I would like to get the internet on my wlan0 and then do the PXE server on my eth0 card. I cannot get this to work after trying several tutorials. :S 

If you need more information ask away.

---

### Post by dandnsmith on 2011-05-23
Have you got any of the bits working in isolation? If so, which?

I'm not sure why you want to separate the 2 functions anyway - you might be creating an unnecessary problem for yourself.

---

### Post by boethius on 2011-05-24
> **Guerreiro said:**
>  I would like to get the internet on my wlan0 and then do the PXE server on my eth0 card. I cannot get this to work after trying several tutorials. :S 

If you need more information ask away.
Based on the limited information provided I am assuming you want to run DHCP and TFTP for PXE boot support on eth0. 

This shouldn't be hard; e.g.,
```
sudo apt-get -y install tftpd-hpa isc-dhcp-server syslinux
```

Hypothetical TFTP server config in /etc/default/tftpd-hpa:
```
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"

```

Hypothetical DHCP server startup config in /etc/default/isc-dhcp-server
```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

```
Hypothetical DHCP server config for PXE network booting (in /etc/dhcp/dhcpd.conf): 
```
ddns-update-style none;
option domain-name "test.com";
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7;
next-server 192.168.56.1;
filename "pxelinux.0"; 

subnet 192.168.1.0 netmask 255.255.255.0 {
  option routers 192.168.1.254;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 800;
}

subnet 192.168.56.0 netmask 255.255.255.0 {
  option routers 192.168.56.1;
  option broadcast-address 192.168.56.255;
  range 192.168.56.100 192.168.56.200;
  default-lease-time 600;
  max-lease-time 800;
}

```
Of course the DHCP server configuration will depend on your actual network configuration - this is merely a working example. 

Also be mindful of local firewalls that could block DHCP broadcasts and/or TFTP requests - ufw is frequently used in Ubuntu but a quick "iptables -L -n" will show you if there are any existing iptables rules or policies.  If there are you should flush them out and set a default "accept" policy for the IN, OUT, and FORWARD chains to eliminate that as a possibility.

---

