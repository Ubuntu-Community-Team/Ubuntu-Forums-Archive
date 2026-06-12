---
title: "Setting up a Firewall, Gateway, DHCP Server, Proxy Server, DNS Caching Server"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by cptmorgan175 on 2008-12-09
The purpose of this post is to provide a “How To” guide for assembling and configuring a Firewall, Gateway, DHCP Server, Proxy Server, DNS Caching Server in Ubuntu 8.10 ”Intrepid”


Here is the hardware we chose for our machine:

 Intel D945GCL2 motherboard  with integrated LAN, video and processor([http://www.intel.com/Products/Desktop/Motherboards/D945GCLF2/D945GCLF2-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/D945GCLF2/D945GCLF2-overview.htm))
10/100/1000  PCI network card
 2 gigabyte stick of so-dim RAM 
 750 gigabyte  SATA hard drive
DVD writer/ reader
Apex MI-100 mini-itx case([http://www.apextechusa.com/products.asp?pID=115](http://www.apextechusa.com/products.asp?pID=115))

  Once the hardware was installed in the computer case  we proceeded to install Ubuntu 8.10 "Intrepid" using a live CD. At this point a decision needs to be made as to whether the entire hard drive is going to be used for the file system or if only a part of it will be used.  If only part of the hard drive will be used, a possible option is to use the extra space as a recovery partition for the device using the g parted application([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) . This came in handy after we reinstalled the system for the third time. Do not forget to update the software using the update manager . 

  We decided to install a sensor suite  for the motherboard and hard drive to help us monitor the vital statistics of the system ([http://www.techthrob.com/tech/linuxsensors.php](http://www.techthrob.com/tech/linuxsensors.php)) . Plus, when we were testing our proxy server we could see whether the traffic was coming from the hard drive or the network card. 

	code: “sudo apt-get install lmsensors”

   Next install the sensor suite for the hard drive 

	code :”sudo apt-get install hddtemp"

   Now you need to see which sensors are available 

code :"sudo sensors-detect"

  Proceed to activate the  sensors by running the sensors command from a terminal window
because we want to provide a visual output to be placed on the desktop we will install the sensor	
applet.

 code:"sudo apt-get install sensors-applet"

  Next we installed Preload ([http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php)), which cached common applications  into  memory so that they will launch faster. Preload does not require configuration , you just install it and it does it's magic in the background

	 code:"sudo apt-get install preload"

  We elected to use a combination of BIND9 and SQUID to do the DNS resolution caching and the 	HTTP caching 
	code: "sudo apt-get install Bind9"

  This will install the BIND daemon, however it must also be noted that BIND will disable the network manager that is installed by default with Ubuntu so from here on out all network configurations will have to be done using a terminal window. 

  For our system to use the DNS caching we configured the browser to look first on the local host prior to making a DNS lookup.  Type “sudo gedit /etc/resolv.conf” and edit the file to look like the following.
 
domain localdomain
search   localdomain
nameserver 127.0.0.1

 Save the file and then type “sudo chattr -i  /etc/resolv.conf” to lock the file to prevent it from changing otherwise your DNS server will not function properly.

 You can test BIND9  by doing an nslookup to verify that the DNS info is being cached or by using the dig command. Example “dig yahoo.com”. The query on the second time around should take one or two seconds.

  Because in this setup the on board LAN "eth0" card will receive an ip from the device provided from the ISP and the external lan card"eth1" will provide ip's for the internal network we need to install a DHCP server for the internal LAN this will be accomplished using DCHP3

	code:"sudo apt-get install dhcp3-server"

  Now we need to tell the  DHCP server which network card to listen to by editing the “sudo gedit /etc/default/dhcp3-server” file.   At the bottom the line marked as INTERFACES=""needs to have eth1 added to it, then save the file .

Example:

# Defaults for dhcp initscript 
# sourced by /etc/init.d/dhcp 
# installed at /etc/default/dhcp3-server by the maintainer scripts 

# 
# This is a POSIX shell fragment 
# 

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests? 
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1". 
INTERFACES="eth1"

save the file. 

 Type the command “sudo gedit /etc/dhcp3/dhcpd.conf”. This file provides the configuration parameters for the DHCP server. We need to make this server “authoritative”. One trick is to hit the “Ctrl-F” key combination to open a search box. Search for “authoritative” and uncomment the line by deleting the pound sign. Then search for “a slightly different configuration for an internal subnet”. This  is where the gateway address, ip range, subnet mask, broadcast address, default lease and max lease time is set for the internal LAN DHCP server. The rest of the file should keep the default settings.

Example:
# 
# Sample configuration file for ISC dhcpd for Debian 
# 
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as 
# configuration file instead of this file. 
# 
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $ 
# 

# The ddns-updates-style parameter controls whether or not the server will 
# attempt to do a DNS update when a lease is confirmed. We default to the 
# behavior of the version 2 packages ('none', since DHCP v2 didn't 
# have support for DDNS.) 
ddns-update-style none; 

# option definitions common to all supported networks... 
#option domain-name "example.org"; 
#option domain-name-servers ns1.example.org, ns2.example.org; 

#default-lease-time 600; 
#max-lease-time 7200; 

# If this DHCP server is the official DHCP server for the local 
# network, the authoritative directive should be uncommented. 
authoritative; 

# Use this to send dhcp log messages to a different log file (you also 
# have to hack syslog.conf to complete the redirection). 
log-facility local7; 

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology. 

#subnet 10.152.187.0 netmask 255.255.255.0 { 
#} 

# This is a very basic subnet declaration. 

#subnet 10.254.239.0 netmask 255.255.255.224 { 
#  range 10.254.239.10 10.254.239.20; 
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org; 
#} 

# This declaration allows BOOTP clients to get dynamic addresses, 
# which we don't really recommend. 

#subnet 10.254.239.32 netmask 255.255.255.224 { 
#  range dynamic-bootp 10.254.239.40 10.254.239.60; 
#  option broadcast-address 10.254.239.31; 
#  option routers rtr-239-32-1.example.org; 
#} 
 


# internal network eth1 (wired network) 
# a slightly different configuration for an internal subnet
subnet 192.168.0.0 netmask 255.255.255.0 { 
range 192.168.0.100 192.168.0.150; 
option domain-name-servers 192.168.0.1; 
option domain-name "Toaster.net"; 
option routers 192.168.0.1; 
option broadcast-address 192.168.0.255; 
default-lease-time 600; 
max-lease-time 7200; 
} 

# internal network eth2 (wireless network) 
#subnet 192.168.20.0 netmask 255.255.255.0 { 
#range 192.168.20.100 192.168.20.150; 
#option domain-name-servers 192.168.20.1; 
#option domain-name “toaster.net”; 
#option routers 192.168.20.1; 
#option broadcast-address 192.168.20.255; 
#default-lease-time 600; 
#max-lease-time 7200; 
#} 

# hosts which require special configuration options can be listed in 
# host statements.   If no address is specified, the address will be 
# allocated dynamically (if possible), but the host-specific information 
# will still come from the host declaration. 
#host passacaglia { 
#  hardware ethernet 0:0:c0:5d:bd:95; 
#  filename "vmunix.passacaglia"; 
#  server-name "toccata.fugue.com"; 
#} 

# Fixed IP addresses can also be specified for hosts.   These addresses 
# should not also be listed as being available for dynamic assignment. 
# Hosts for which fixed IP addresses have been specified can boot using 
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only 
# be booted with DHCP, unless there is an address range on the subnet 
# to which a BOOTP client is connected which has the dynamic-bootp flag 
# set. 
#host fantasia { 
#  hardware ethernet 08:00:07:26:c0:a5; 
#  fixed-address fantasia.fugue.com; 
#} 

After changes have been made save the file.

Type  “sudo /etc/init.d/dhcp3-server restart” to restart the internal LAN DHCP server on “eth1”

  Next we need to modify the firewall to forward all packets from “eth1” to “eth0” and to block all unwanted inbound traffic. Here is a basic firewall that we found ([http://www.debian-administration.org/articles/23](http://www.debian-administration.org/articles/23))

#!/bin/bash 

PATH=/usr/sbin:/sbin:/bin:/usr/bin 

# 
# delete all existing rules 
# 
iptables -F 
iptables -t nat -F 
iptables -t mangle -F 
iptables -X 

# Always accept loopback traffic 
iptables -A INPUT -i lo -j ACCEPT 


# Allow established connections, and those not coming from the outside 
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A INPUT -m state --state NEW -i ! eth0 -j ACCEPT 
iptables -A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED 
 
# ALLOW outgoing connections from the LAN side 
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT 

# Maquerade. 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 

# Don't forward from the outside to the inside. 
iptables -A FORWARD -i eth0 -o eth0 -j REJECT 

# Enable routing 
echo 1 > /proc/sys/net/ipv4/ip_forward

  Save the file with a name like _firewall or 00-firewall. Place the firewall in the file system directory  /etc/network/if-up.d/ so it will turn on as soon as your computer boots up. Make sure the file is executable by typing “sudo chmod -x /etc/network/if-up.d/_firewall” 
  Now the computers attached to the lan side “eth1” of your gateway should be able to surf the internet via “eth0”. 
  We installed a  proxy server called “SQUID” on our gateway to reduce the amount of bandwidth consumed by HTTP traffic. SQUID  improves response times by caching and reusing frequently-requested web pages. Type “sudo apt-get install squid” to install the free version of squid onto your machine. There are two ways to go from here. You can configure the proxy settings in each client's browser to use the proxy server.([http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/](http://sylvarwolflinux.wordpress.com/2007/12/18/installing-squid-proxy-server-in-ubuntu/))
Set the HTTP proxy to 192.168.0.1    PORT 3128
   Or you can configure a transparent proxy by adding a line of code anywhere on your firewall a.k.a “iptables”
  Type “sudo gedit /etc/network/if-up.d/_firewall” then copy and paste this line of code into the file.
# Forward all packets through Squid to save bandwidth
iptables -t nat -A PREROUTING -i eth1 -p tcp –dport 80 -d ! 192.168.0.0/255.255.255.0 -j REDIRECT –to-port 3128
 This should complete the installation and configuring of a Firewall, Gateway, DHCP Server, Proxy Server, DNS Caching Server.
For ease of maintenance and administration we installed Open ssh server.

Code “sudo apt-get install openssh-server”

This will allow for administering the gateway remotely  a.ka  with out the need for a monitor, keyboard and mouse([https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html))

---

### Post by WhoopGetOut on 2009-02-06
Ok, so I must be missing something.  I have everything configured as you have gone over, but I'm not sure if it is working or not.  If I set up a proxy in my browser I can go to my squid3 access.log file and every site that I browse to shows up in that file, but without the proxy set up within the browser (transparent) I get nothing in the access.log file.  Is this normal?  Is there another way to see if this is working correctly?  Will I still be able to monitor web traffic through this file or some other file?  Thanks in advance.

---

### Post by mohitchawla on 2009-02-06
Why not use Webmin instead (for the configuration) ?!

---

### Post by jongers on 2010-06-16
> **mohitchawla said:**
> Why not use Webmin instead (for the configuration) ?!
Sorry to butt in on [cptmorgan175]("http://ubuntuforums.org/member.php?u=724099").

Webmin is a very good configuration manager.  But for a secure and robust system it's best to keep the additional programs limited.
Also if you read most of the configuration files you can learn about extra setting and functionalities of programs.

if Everyone puts Howtos as good as this only, no one should ever need webmin again.  Thanks [cptmorgan175]("http://ubuntuforums.org/member.php?u=724099")

---

### Post by mirza_farid on 2010-06-20
why not use the manual by connection icon!!:confused:

---

### Post by ubunutucyclotron on 2010-07-01
Hi cptmorgan175.

Thanks for this little explanation, I have never been able to get dhcp working on linux before however I did once years ago setup a linux firewall (redhat) with static ips. However it is 1.15am so before going to bed I need to ask for help to get this working fully.

I have done everything as you've said. All I've changed is the network from 192.x to 10.1.1.1 with that being my dhcp server and the domain from toaster.net to nunsurfer.net. (My server is a surfing nun) The dhcp server works and is handing out ips. The clients are taking ips. The machines can ping each other, however when I ping co.za from a client, while the name is resolved correctly to 206.223.136.173 the pings do not come back. When I ping co.za from the server the pings come back so I know they can. Of course I cannot surf.

Years ago I think the magic line to get my firewall working was something like the "echo 1 > /proc/sys/net/ipv4/ip_forward" line as the forwarding was all I needed to get it working. However this time it just does not work! When I cat that file it always says 0. Is it supposed to say 1? I have run the command to make the 00-firewall file executable.

I've also noticed that despite running the lock command on resolv.conf it still changes from what you put to the two nameservers my service provider uses. While I find this odd (that the locking seems to fail) the resolving of names seems to be working, I'm sure the problem is with forwarding.

eth0 is connected to the modem and eth1 is connected to my lan so the firewall file is applicable.

Help.

EDIT: Shouldn't sudo chmod -x /etc/network/if-up.d/_firewall actually be sudo chmod +x /etc/network/if-up.d/_firewall  ???

---

