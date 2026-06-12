---
title: "Sharing internet between two Ubuntus"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by damnated on 2010-12-27
I have a desktop PC and a laptop, both running Ubuntu lucid, the laptop has XFCE and the PC has GNOME, but that's actually not relevant.

My PC is connected to the internet through an USB modem in eth1, and I wanted to share this connection through the PC's network card. I followed this [https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20%28iptables%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu%20Internet%20Gateway%20Method%20%28iptables%29) tutorial.
I can't access the internet from my laptop, but whenever I connect the two machines with a network cable, my PC sees the connection at eth0 (even announces connection and disconnection), but my laptop does not.

I have no idea what's going on, could this be a faulty cable or a faulty network card at my laptop? Or I simply screwed up the connection setup? Please advise!

---

### Post by damnated on 2011-01-01
bump.

---

### Post by spiky001 on 2011-01-01
Have you tried setting the network connection between the 2 machines in network manager to shared to other pc,s

---

### Post by damnated on 2011-01-01
> **spiky001 said:**
> Have you tried setting the network connection between the 2 machines in network manager to shared to other pc,s
I did with my eth1 connection (my internet connection) on the PC. Should I share the connection between the two machines as well?

---

### Post by spiky001 on 2011-01-01
Yes the 1 the two machines use in the ipv4 settings

---

### Post by damnated on 2011-01-01
Hmm, this is interesting. I set the connection between the two machines as shared. Now my laptop sees the connection, but there's no internet.

I also learned that my internet connection was set to Automatic (DHCP). If I set this connection to shared, I can't connect to the internet.

---

### Post by spiky001 on 2011-01-01
My internet is set to auto eth0 +wlan0 connections set to shared

---

### Post by damnated on 2011-01-01
This is how it is: 

PC:
Auto eth0 (connected to laptop) is shared
Auto eth1 (internet) is Automatic (DHCP) 

laptop:
Auto eth0 (connect to PC) is shared

All 3 are active, yet I still can't connect to the internet from the laptop.

---

### Post by spiky001 on 2011-01-01
Set laptop eth0 to automatic. Just check you have the compatible ip addresses on both machines

---

### Post by damnated on 2011-01-01
> **spiky001 said:**
> Set laptop eth0 to automatic. Just check you have the compatible ip addresses on both machines
Hah, if I set it to automatic, it can't connect.

---

### Post by spiky001 on 2011-01-01
Have you checked ifconfig of both machines, you should have ip address should be on same internal ip range

---

### Post by perspectoff on 2011-01-01
Use Internet bridging.

See Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Network_Interfaces_Bridging](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Network_Interfaces_Bridging)

or Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#Network_Interfaces_Bridging](http://kubuntuguide.org/Maverick#Network_Interfaces_Bridging)


Ooops. Wrong article. I meant Internet Connection Sharing:

See Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Internet_connection_sharing_.28DHCP_server.29](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Internet_connection_sharing_.28DHCP_server.29)

or Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#Internet_connection_sharing_.28DHCP_server.29](http://kubuntuguide.org/Maverick#Internet_connection_sharing_.28DHCP_server.29)

However, my real reply is: you're kidding, right? A wireless-N router is about $35 these days at Best Buy or something. Heck, I probably have that in change in my couch cushions. Unless your USB modem is for a 3G connection, I guess. Hmmm, I wonder if they have routers for 3G connections...

Yep, what do you know? They do. They're about $130, though, like this one:

[http://www.google.com/products/catalog?hl=en&q=3g+routers&um=1&ie=UTF-8&cid=17927545339932895004&ei=MMMfTbenIYG6sQPl3rzRAg&sa=X&oi=product_catalog_result&ct=result&resnum=4&ved=0CEkQ8wIwAw&output=nojs](http://www.google.com/products/catalog?hl=en&q=3g+routers&um=1&ie=UTF-8&cid=17927545339932895004&ei=MMMfTbenIYG6sQPl3rzRAg&sa=X&oi=product_catalog_result&ct=result&resnum=4&ved=0CEkQ8wIwAw&output=nojs)

---

### Post by damnated on 2011-01-01
> **spiky001 said:**
> Have you checked ifconfig of both machines, you should have ip address should be on same internal ip range

I have ```
eth0      Link encap:Ethernet  HWaddr 00:13:8f:ec:0d:f4  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:feec:df4/64 Scope:Link 
          (...)
``` on the PC but I don't have an internal address for the laptop : ```

eth0      Link encap:Ethernet  HWaddr 90:fb:a6:e3:7f:aa  
          inet6 addr: fe80::92fb:a6ff:fee3:7faa/64 Scope:Link
```

How can I set an internal address?

---

### Post by PatchesTheCaveman on 2011-01-01
Go to Applications > Accessories > Terminal on your top panel.  Then, in the black box that pops up, type this in and press Enter:
```
sudo apt-get install firestarter dhcp3-server
```
Enter your password and say yes to install those programs and all the other programs they'll need to function.

Now you can set up Internet sharing. Go to Applications > Internet > Firestarter.  I believe the Welcome to Firestarter screen will pop up when you first run it but if not go to Firewall > Run Wizard.

Click Forward.  Under *Please select your Internet connected network device* select your Internet connected interface.  Make sure *IP Address is assigned by DHCP* is checked.  Click Forward.

Check *Enable Internet connection sharing*.  Choose *eth0* as the *Local area nework device*.  Check *Enable DHCP for local network*.  Click Forward.

Make sure *Start firewall now* is checked and click Save.  Your Ubuntu machine is now configured to share the Internet with your Windows machines and any others on the network.

---

### Post by damnated on 2011-01-01
> **PatchesTheCaveman said:**
> 
Check *Enable Internet connection sharing*.  Choose *eth0* as the *Local area nework device*.  Check *Enable DHCP for local network*.  Click Forward.
The option for enabling DHCP for local network is grayed out. DHCP server was installed, of course.

---

### Post by PatchesTheCaveman on 2011-01-01
Finish the wizard like I said without enabling DHCP.

After that, go to Edit > Preferences.  Click *Network Settings* under *Firewall* on the left.  Check *Enable DHCP for the local network*.  Click on the arrow next to *DHCP server details* to reveal the additional DHCP options.  Click the *Create new DHCP configuration* radio button.  Leave the rest of the settings at their default.

After you've done all that, click *Accept*.  Then go to Firewall > Start Firewall.

---

### Post by damnated on 2011-01-01
It encounters an error. "Failed to start firewall, an unknown error occurred. Please check your network device settings and make sure your Internet connection is active."

---

### Post by PatchesTheCaveman on 2011-01-01
Open a teriminal window and run this command to start Firestarter:
```
gksudo firestarter
```

Stop and start the firewall.  Error messages from firestarter should appear in the terminal window.  Copy and paste them in a reply to this thread.

---

### Post by damnated on 2011-01-01
```
$ gksudo firestarter
Firewall started
Failed to start DHCP server
```if I run the wizard again, this is also the only error I get in the terminal.

---

### Post by PatchesTheCaveman on 2011-01-01
Run these commands and copy/paste the output:
```
cat /etc/dhcp3/dhcpd.conf
sudo cat /var/log/syslog | grep -i dhcp
ifconfig -a
```

---

### Post by damnated on 2011-01-02
```

$ cat /etc/dhcp3/dhcpd.conf
# DHCP configuration generated by Firestarter
ddns-update-style interim;
ignore client-updates;

subnet 10.42.43.0 netmask 255.255.255.0 {
    option routers 10.42.43.1;
    option subnet-mask 255.255.255.0;
    option domain-name-servers 213.154.124.1, 193.231.252.1;
    option ip-forwarding off;
    range dynamic-bootp 192.168.0.100 192.168.0.254;
    default-lease-time 21600;
    max-lease-time 43200;
}

```

```

$ sudo cat /var/log/syslog | grep -i dhcp
Jan  2 01:33:13 damnated-desktop NetworkManager: <debug> [1293924793.351777] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 01:33:13 damnated-desktop dnsmasq[8629]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 01:33:13 damnated-desktop dnsmasq-dhcp[8629]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 01:34:41 damnated-desktop NetworkManager: <debug> [1293924881.803014] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 01:34:41 damnated-desktop dnsmasq[9393]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 01:34:41 damnated-desktop dnsmasq-dhcp[9393]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 01:52:44 damnated-desktop NetworkManager: <info>  (eth1): canceled DHCP transaction, dhcp client pid 2984
Jan  2 01:58:14 damnated-desktop NetworkManager: <debug> [1293926294.681212] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 01:58:14 damnated-desktop dnsmasq[10433]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 01:58:14 damnated-desktop dnsmasq-dhcp[10433]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 01:58:20 damnated-desktop dnsmasq-dhcp[10433]: DHCPDISCOVER(eth0) 90:fb:a6:e3:7f:aa 
Jan  2 01:58:20 damnated-desktop dnsmasq-dhcp[10433]: DHCPOFFER(eth0) 10.42.43.10 90:fb:a6:e3:7f:aa 
Jan  2 01:58:20 damnated-desktop dnsmasq-dhcp[10433]: DHCPREQUEST(eth0) 10.42.43.10 90:fb:a6:e3:7f:aa 
Jan  2 01:58:20 damnated-desktop dnsmasq-dhcp[10433]: DHCPACK(eth0) 10.42.43.10 90:fb:a6:e3:7f:aa damnated-laptop
Jan  2 02:02:12 damnated-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Jan  2 02:02:12 damnated-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  2 02:02:12 damnated-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 02:02:12 damnated-desktop NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
Jan  2 02:02:12 damnated-desktop dhclient: DHCPREQUEST of 86.125.157.175 on eth1 to 255.255.255.255 port 67
Jan  2 02:02:12 damnated-desktop dhclient: DHCPACK of 86.125.157.175 from 86.125.157.161
Jan  2 02:02:12 damnated-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
Jan  2 02:02:24 damnated-desktop NetworkManager: <debug> [1293926544.566325] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 02:02:24 damnated-desktop dnsmasq[11068]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 02:02:24 damnated-desktop dnsmasq-dhcp[11068]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 02:09:56 damnated-desktop NetworkManager: <debug> [1293926996.214584] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 02:09:56 damnated-desktop dnsmasq[12329]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 02:09:56 damnated-desktop dnsmasq-dhcp[12329]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 02:35:48 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 02:35:48 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 02:35:48 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 02:35:48 damnated-desktop dhcpd: All rights reserved.
Jan  2 02:35:48 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 02:35:48 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 02:36:16 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 02:36:16 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 02:36:16 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 02:36:16 damnated-desktop dhcpd: All rights reserved.
Jan  2 02:36:16 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 02:36:16 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 02:36:28 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 02:36:28 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 02:36:28 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 02:36:28 damnated-desktop dhcpd: All rights reserved.
Jan  2 02:36:28 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 02:36:28 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 02:38:20 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 02:38:20 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 02:38:20 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 02:38:20 damnated-desktop dhcpd: All rights reserved.
Jan  2 02:38:20 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 02:38:20 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:45:28 damnated-desktop NetworkManager: <debug> [1293932728.936172] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 03:45:29 damnated-desktop dnsmasq[20457]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 03:45:29 damnated-desktop dnsmasq-dhcp[20457]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 03:45:30 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:45:30 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 03:45:30 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 03:45:30 damnated-desktop dhcpd: All rights reserved.
Jan  2 03:45:30 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 03:45:30 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:45:34 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:45:34 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 03:45:34 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 03:45:34 damnated-desktop dhcpd: All rights reserved.
Jan  2 03:45:34 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 03:45:34 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:46:09 damnated-desktop NetworkManager: <debug> [1293932769.159081] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 03:46:09 damnated-desktop dnsmasq[21301]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 03:46:09 damnated-desktop dnsmasq-dhcp[21301]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 03:46:09 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:46:09 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 03:46:09 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 03:46:09 damnated-desktop dhcpd: All rights reserved.
Jan  2 03:46:09 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 03:46:09 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:46:24 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:46:24 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 03:46:24 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 03:46:24 damnated-desktop dhcpd: All rights reserved.
Jan  2 03:46:24 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 03:46:24 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:46:37 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 03:46:37 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 03:46:37 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 03:46:37 damnated-desktop dhcpd: All rights reserved.
Jan  2 03:46:37 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 03:46:37 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 13:15:01 damnated-desktop kernel: [   19.933353] type=1505 audit(1293966900.725:3):  operation="profile_load" pid=623 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan  2 13:15:01 damnated-desktop kernel: [   20.587121] type=1505 audit(1293966901.377:11):  operation="profile_load" pid=795 name="/usr/sbin/dhcpd3"
Jan  2 13:15:02 damnated-desktop NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction (timeout in 45 seconds)
Jan  2 13:15:02 damnated-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  2 13:15:02 damnated-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 13:15:02 damnated-desktop NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit
Jan  2 13:15:03 damnated-desktop dhclient: DHCPREQUEST of 86.125.157.175 on eth1 to 255.255.255.255 port 67
Jan  2 13:15:03 damnated-desktop dhclient: DHCPACK of 86.125.157.175 from 86.125.157.161
Jan  2 13:15:03 damnated-desktop NetworkManager: <info>  DHCP: device eth1 state changed preinit -> reboot
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: All rights reserved.
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: 
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Please contribute if you find this software useful.
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: 
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Configured subnet: 172.16.101.0
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.101.254
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Recving on     VNet/vmnet1/172.16.101.0
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Sending on     VNet/vmnet1/172.16.101.0
Jan  2 13:15:03 damnated-desktop kernel: [   22.370090] /dev/vmnet: open called by PID 1150 (vmnet-dhcpd)
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: All rights reserved.
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: 
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Please contribute if you find this software useful.
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: 
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Configured subnet: 192.168.103.0
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.103.254
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Recving on     VNet/vmnet8/192.168.103.0
Jan  2 13:15:03 damnated-desktop vmnet-dhcpd: Sending on     VNet/vmnet8/192.168.103.0
Jan  2 13:15:03 damnated-desktop kernel: [   22.464343] /dev/vmnet: open called by PID 1155 (vmnet-dhcpd)
Jan  2 13:15:03 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 13:15:03 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 13:15:03 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 13:15:03 damnated-desktop dhcpd: All rights reserved.
Jan  2 13:15:03 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 13:15:03 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 13:18:20 damnated-desktop NetworkManager: <debug> [1293967100.287070] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-eth0.pid
Jan  2 13:18:20 damnated-desktop dnsmasq[2303]: compile time options: IPv6 GNU-getopt DBus I18N DHCP TFTP
Jan  2 13:18:20 damnated-desktop dnsmasq-dhcp[2303]: DHCP, IP range 10.42.43.10 -- 10.42.43.100, lease time 1h
Jan  2 13:18:21 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 13:18:21 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 13:18:21 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 13:18:21 damnated-desktop dhcpd: All rights reserved.
Jan  2 13:18:21 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 13:18:21 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 13:20:13 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0
Jan  2 13:20:13 damnated-desktop dhcpd: Internet Systems Consortium DHCP Server V3.1.3
Jan  2 13:20:13 damnated-desktop dhcpd: Copyright 2004-2009 Internet Systems Consortium.
Jan  2 13:20:13 damnated-desktop dhcpd: All rights reserved.
Jan  2 13:20:13 damnated-desktop dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jan  2 13:20:13 damnated-desktop dhcpd: bad range, address 192.168.0.100 not in subnet 10.42.43.0 netmask 255.255.255.0

```

```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:8f:ec:0d:f4  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:feec:df4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1026 (1.0 KB)  TX bytes:2279 (2.2 KB)
          Interrupt:17 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:14:f8:e7:90:6c  
          inet addr:86.125.157.175  Bcast:86.125.157.191  Mask:255.255.255.224
          inet6 addr: fe80::214:f8ff:fee7:906c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4075715 (4.0 MB)  TX bytes:819929 (819.9 KB)

ham0      Link encap:Ethernet  HWaddr ea:93:c0:b5:d6:85  
          inet addr:5.5.64.104  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:1452 (1.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67612 (67.6 KB)  TX bytes:67612 (67.6 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.101.1  Bcast:172.16.101.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.103.1  Bcast:192.168.103.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by PatchesTheCaveman on 2011-01-02
You've configured everything to use the 10.42.43.0/16 subnet except the IP addresses DHCP assigns to the other computers.

Change the *range dynamic-bootp* line in /etc/dhcp3/dhcpd.conf file to something like this:
```
range dynamic-bootp 10.42.43.10 10.42.43.254;

```
so it assigns IP addresses from that pool and restart your firewall and see if works then.

---

### Post by damnated on 2011-01-02
> **PatchesTheCaveman said:**
> You've configured everything to use the 10.42.43.0/16 subnet except the IP addresses DHCP assigns to the other computers.

Change the *range dynamic-bootp* line in /etc/dhcp3/dhcpd.conf file to something like this:
```
range dynamic-bootp 10.42.43.10 10.42.43.254;

```so it assigns IP addresses from that pool and restart your firewall and see if works then.
The range dynamic-bootp was 192.168.0.100 192.168.0.254; as soon as I changed that, and restarted the firewall the internet is working on my laptop as well. 
Thank you very much for your help!

---

