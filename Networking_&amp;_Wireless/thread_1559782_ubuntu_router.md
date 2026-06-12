---
title: "ubuntu router"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by dschuett on 2010-08-24
I have followed this tutorial to the T, I am able to ping the internet with the router and ping the clients with the router. The clients get an IP address from the router (dhcp3) and the gateway shows 192.168.0.201 and netmask of 255.255.255.0 (eth1 - the internal nic on the router) but the clients can't ping the router (192.168.0.201) nor the internet (eth0). I know this has something to do with routing or IPTABLES, but i am completely new to this and any help is appreciated. 

Also here is what route -n shows:
NOTE: what is with the 169.254.0.0 address???
and shouldn't i see 192.168.0.201 as a gateway???

Kernel IP routing table
Destination     Gateway         Genmask            Flags   Metric     Ref    Use    Iface
192.168.0.0     0.0.0.0            255.255.255.0      U         1             0        0       eth1
68.13.40.0       0.0.0.0            255.255.248.0      U         1             0        0       eth0
169.254.0.0     0.0.0.0            255.255.0.0          U          1000     0        0       eth0
0.0.0.0              68.13.40.1      0.0.0.0                   UG       0            0        0       eth0

TUTORIAL STARTS HERE:
How to make Ubuntu/Debian as a router

Here is your Ubuntu serve box with two interfaces,

eth0-------------Internet (set up with dhcp)
eth1-------------Internal

Note: Your Internet is running using eth0.

Step1: Install DHCP Server

#apt-get install dhcp3-server

Step 2: Configure the DHCP server

Edit the /etc/dhcp3/dhcpd.conf file and add your domain, ip range and other options.
    NOTE: these are the only things i changed:
  
      option domain-name "host name of my router";
      #
      # Internal network
      #
      subnet 192.168.0.0 netmask 255.255.255.0 {
      range 192.168.0.100 192.168.0.200;
      option broadcast-address 192.168.0.255;
      option routers 192.168.0.201;
      default-lease-time 600;
      max-lease-time 7200;
      }

Edit the /etc/default/dhcp3-server

INTERFACES= “eth1”

Step 3: Configure the Internal interface (eth1) with static IP.
 
Edit the /etc/network/interfaces file and add following

iface eth1 inet static
address 192.168.0.201
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.201

Step 4: Restart network and verify the eth1 interface's IP.

#/etc/init.d/network restart

check ip by ifconfig eth1, it will have 192.168.0.201 ip, if not please restart the interface/network service, you can also restart your machine if it is not in production environment.

Step 5: Restart the DHCP server.

#/etc/init.d/dhcp3-server restart

If everything is ok, it should run successfully,
Note: If your interface does not have any IP it might give error and does not restart, first configure your internal interface.

Step 6: Test the DHCP server.

connect the cable on interface eth1 and other side to your switch and connect your second pc, you will get the IP from 192.168.0.xxx range.

Open the syslog messeges with

#tail -f /var/log/syslog

of your debian box, it will also notify with leased ip and detail of requested machine.

Step 7: Enable forwarding

# echo 1 > /proc/sys/net/ipv4/ip_forward

open the file manually and uncomment

# nano /etc/sysctl.conf
net.ipv4.ip_forward = 1

Step 8: Add IPTABLES rule for NAT
 
Type following at command line

#iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
       
Step 9: Final Testing

      Your second Pc attached to LAN have internal ip, ping to a web address and you should get a reply!

---

