---
title: "IP Address always change"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by ManzTiara on 2009-11-22
Dear Ubuntuers ...

We have an IP address that when started up always changed event we already make static configuration. We doesn't use the DHCP reservation to manage my IP.

Here my configuration :
from /etc/network/interfaces : 
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.15
netmask 255.255.255.0
gateway 192.168.1.200

/etc/resolv.conf :
nameserver 192.168.1.1

every time when my system startup, the IP always change even in range 192.168.1.1 ~ x.x.x.254, and routing table is empty.

but, when i running at my shell :

sudo /etc/init.d/networking restart 

my eth0 will come into 192.168.1.15 and routing table no empty.

Does anyone can resolve this matter ?

TIA

---

### Post by Iowan on 2009-11-23
Hmmm... wonder if Network Manager is involved (it *should* ignore interface defined in */etc/network/interfaces*)
One thing to try - Edit settings under Network Manager for Auto eth0. Un-check the "Connect automatically" box and restart/reboot. 

This probably won't work, but worth a quick try...

---

### Post by ManzTiara on 2009-11-24
Hi Iowan, in my NetworkManager doesn't show my Auto eth0. In my network connection, this setting is disabled for button Edit and Delete.

In NetworkManager only show : 
Wired network 
device not manager

Wireless network
disconnected

and also, the wireless connection name is weird.

---

### Post by Iowan on 2009-11-25
That's probably a good thing - looks like NM is ignoring eth0. I don't have Karmic, so I'm not sure how to check if/when **ifconfig** might get run. I'd rather not suggest removing it... yet.
There are probably ways to handicap **ifconfig** so it doesn't actually do anything (comment out the "request" line in */etc/dhcp3/dhclient.conf*).

---

### Post by ManzTiara on 2009-12-02
I'm just change into WICD, but same already set with static addresses, always get the dhcp addresses.

in my dhclient.conf already commenting out, here my dhclient.conf :

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "Manz";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
#request subnet-mask, broadcast-address, time-offset, routers,
#    domain-name, domain-name-servers, domain-search, host-name,
#    netbios-name-servers, netbios-scope, interface-mtu,
#    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
timeout 20;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.168.1.15;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.168.1.15;
#  medium "link0 link1";
#  option host-name "192.168.1.2";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.168.1.255;
#  option routers 192.168.1.200;
#  option domain-name-servers 192.168.1.2;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

for /var/lib/dhcp3/dhclient.leases :

#lease {
#  interface "eth0";
#  fixed-address 192.1.168.101;
#  option subnet-mask 255.255.255.0;
#  option dhcp-lease-time 604800;
#  option dhcp-message-type 5;
#  option dhcp-server-identifier 192.168.1.2;
#  option domain-name-servers 192.168.1.2;
#  option dhcp-renewal-time 302400;
#  option dhcp-rebinding-time 529200;
#  renew 4 2009/12/03 03:12:14;
#  rebind 4 2009/12/03 03:12:14;
#  expire 4 2009/12/03 03:12:14;
#}

but always produces : /var/run/connman/dhclient.eth0.leases
lease {
  interface "eth0";
  fixed-address 192.168.1.101;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 604800;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.1.2;
  option dhcp-server-identifier 192.168.1.2;
  option dhcp-renewal-time 302400;
  option dhcp-rebinding-time 529200;
  renew 0 2009/12/06 14:34:20;
  rebind 3 2009/12/09 06:13:46;
  expire 4 2009/12/10 03:13:46;
}

I didn't know how to resolve this things.... :confused:

so, if we want to use 192.168.1.15 , always running : sudo /etc/init.d/networking restart...

weird #-o

---

