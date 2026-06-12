---
title: "Configuring LTSP network/DHCP server"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by pixel :-) on 2012-02-25
I'm trying to have a LTSP server with a single client. I have one wireless that connects to the internet, and intent to use the ethernet for the conection to the other PC. 

The documentation is a bit old. I'm on kubntu 11.10, everything upgraded.

For simplicity, i'm asking here how to do it with a virtuall box machine.

I believe the virtual machine it self is configured corectly. I followed this [http://www.thefanclub.co.za/how-to/how-create-virtualbox-ubuntu-ltsp-thin-client]("http://www.thefanclub.co.za/how-to/how-create-virtualbox-ubuntu-ltsp-thin-client")

It sais
> searching for searver DHCP ... No IP. No IP. No IP
(i was carefull with architecture 64 bits)
(The physical computer sais something similar)

at first i did:

> sudo apt-get install ltsp-server-standalone openssh-server

sudo ltsp-build-client

in "/etc/ltsp/dhcpd.conf" it said something about i386 and the paths where wrong.

i changed it to

> authoritative;

subnet 192.168.22.0 netmask 255.255.255.0 {
  range 192.168.22.20 192.168.22.250;
  option domain-name "example.com";
  option domain-name-servers 192.168.22.1;
  option broadcast-address 192.168.22.255;
  option routers 192.168.22.1;
  option subnet-mask 255.255.255.0;

  filename "/opt/ltsp/amd64/boot/pxelinux.0";
  option root-path "/opt/ltsp/amd64";
}


in /etc/default/isc-dhcp-server i put
> INTERFACES=&#8221;eth0&#8243;

in /etc/network/interfaces
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address 192.168.22.1
     netmask 255.255.255.0

and run 

> 
sudo ifup eth0
sudo /etc/init.d/isc-dhcp-server restart
sudo ltsp-update-sshkeys
sudo ltsp-update-image
sudo /etc/init.d/nbd-server restart


Internet is configured on wlan0 DHCP
Knemo tells me

192.168.1.64/24 (i don't know what the 24 stans for)
broadcast adress 192.168.1.255
default gataway 192.168.0.1


it doesn't work. From the log

> 02/25/12 07:48:53 PM	epsilon	dhcpd	Wrote 0 leases to leases file.
02/25/12 07:48:53 PM	epsilon	dhcpd	
02/25/12 07:48:53 PM	epsilon	dhcpd	No subnet declaration for &#8221;eth0&#8243; (no IPv4 addresses).
02/25/12 07:48:53 PM	epsilon	dhcpd	** Ignoring requests on &#8221;eth0&#8243;.  If this is not what
02/25/12 07:48:53 PM	epsilon	dhcpd	   you want, please write a subnet declaration
02/25/12 07:48:53 PM	epsilon	dhcpd	   in your dhcpd.conf file for the network segment
02/25/12 07:48:53 PM	epsilon	dhcpd	   to which interface &#8221;eth0&#8243; is attached. **
02/25/12 07:48:53 PM	epsilon	dhcpd	
02/25/12 07:48:53 PM	epsilon	dhcpd	
02/25/12 07:48:53 PM	epsilon	dhcpd	Not configured to listen on any interfaces!
02/25/12 07:53:44 PM	epsilon	dhclient	DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
02/25/12 07:53:46 PM	epsilon	dhclient	DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
[......]
02/25/12 07:58:28 PM	epsilon	dhclient	DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
02/25/12 07:58:35 PM	epsilon	dhclient	DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
02/25/12 07:58:45 PM	epsilon	dhclient	No DHCPOFFERS received.
02/25/12 07:58:45 PM	epsilon	dhclient	No working leases in persistent database - sleeping.


something is going on.

Thanck you for your time. :popcorn:

---

### Post by pixel :-) on 2012-02-26
bump

---

