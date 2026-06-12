---
title: "No network connection on jaunty (gnome) but working in intrepid (kde)"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by atroq on 2009-05-30
Hi all,

I recently installed Ubuntu Jaunty on a second partition on my system. Strangely, the network connection does not work, the Gnome panel applet simply says there is no connection on eth0. This is a simple wired ethernet connetion to my router which should work over DHCP.

Now what is strange: I have Intrepid installed on a different partition. This was initially a Kubuntu install so the network connection was set up by KDE. Here everything works fine. When I start Gnome on the Intrepid installation, the network of course works as well, but the applet in the gnome panel nevertheless claims there is no connection.

I tried copying over /etc/interfaces to the Jaunty partition, but this did not help. Neither did trying to configure the network manually with a static IP address. This is my /etc/interfaces on the working installation:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.2.4
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    gateway 192.168.2.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 192.168.2.1

Do Gnome and KDE set up the network differently? I have no idea where to start looking.

Thanks a lot in advance for any help!

Jan

---

### Post by superprash2003 on 2009-05-30
change eth0 to dhcp and then type **sudo dhclient eth0** and post output

---

### Post by Iowan on 2009-05-30
> **atroq said:**
>  When I start Gnome on the Intrepid installation, the network of course works as well, but the applet in the gnome panel nevertheless claims there is no connection. That's *probably* because NM isn't managing the connection.  You *should* be able to remove (or comment out) the definition in */etc/network/interfaces* and use the NM applet to configure the interface.

---

### Post by atroq on 2009-05-30
> **superprash2003 said:**
> change eth0 to dhcp and then type sudo dhclient eth0 and post output

Thanks for your reply!

I'm wasn't sure where to change eth0 to dhcp, so I changed my /etc/network/interface to:

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

And ran sudo dhclient eth0. This is what I got:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:d4:5d:ab:69
Sending on   LPF/eth0/00:13:d4:5d:ab:69
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any ideas?

---

### Post by atroq on 2009-05-30
> **Iowan said:**
> That's *probably* because NM isn't managing the connection.  You *should* be able to remove (or comment out) the definition in */etc/network/interfaces* and use the NM applet to configure the interface.

Thanks to you as well for your help.

On my working installation I tried your suggestion just to find out how this works but now I'm even more confused. I commented out the eth0 section in the interfaces file and in the Network Connections application I added a new connection with the Mac address of my network adapter as DHCP and selected "System setting". I said ok and did a /etc/init.d/networking restart just to be sure. Now my network is still working, but the applet still says I'm not connected. I also cannot see the new connection I added in the Network Configuration application - when I left-click the icon in the panel it says the device is unmanaged.

On the non-working installation, the dialog for adding a new connection doesn't even open when I click the button. I remember that is worked once, so maybe the application is confused by some settings I made earlier. Do you know where it keeps its configuration files so I can take a look at them or delete them?

---

### Post by superprash2003 on 2009-05-30
post contents of the /etc/dhcp3/dhclient.conf file

---

### Post by atroq on 2009-05-30
> **superprash2003 said:**
> post contents of the /etc/dhcp3/dhclient.conf file

Here it is. What may not have been apparent in my inital posting is that the Jaunty system is a clean install, so I'd expect the file below to be the default one. 

One addition to my reply to Iowan: After rebooting my working system, the network stopped working there, too. I had to undo my changes to the interfaces file (back to static configuration).

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by Iowan on 2009-05-30
> **atroq said:**
> One addition to my reply to Iowan: After rebooting my working system, the network stopped working there, too. I had to undo my changes to the interfaces file (back to static configuration).
 I was gonna suggest that you might need to restart Network Manager (or reboot).  Apparently the reboot made it worse. :(

---

### Post by superprash2003 on 2009-05-31
try this [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

---

