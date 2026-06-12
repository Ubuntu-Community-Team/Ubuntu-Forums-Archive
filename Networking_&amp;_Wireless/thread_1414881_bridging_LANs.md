---
title: "bridging LANs"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2010-02-24
Hi everyone!

I want to make a bridge between LANs. I wanted to do it with a software called Endian Firewall but the documentation is poor and there is not much  info about it. Therefore, I would like to know a good software to use in order to create that bridge. The simpler, the better. 

PC1--PC2--PC3 |-- Router  --------------INTERNET--------------- Router --|-- PC4--PC5 (LAN B)
 (LAN A)
  

I have read about OpenVPN and learn how to use it, the problem is that when I look solutions for bridging, all of them talk about installing OpenVPN in the Router which I cannot do.

Thanks in advance!

---

### Post by dvlchd3 on 2010-02-24
What are you using for your routers then?  If you are using actual computers running some derviative of Linux, installing OpenVPN should be no problem.  Otherwise, you really only have two options:
(1) - consult the router's documentation for bridging connections
(2) - setup a VPN server within the network and have the router forward any requests for VPN to that server.  This will allow you to follow the solution you mentioned involving OpenVPN, just with a few extra steps added.

I feel the first option is the more secure one, however, if you have to resort to option two, please look into Linux firewalling, especially [iptables]("https://help.ubuntu.com/community/IptablesHowTo").  These will be your friend when it comes to securing your network!

---

### Post by mosquetero on 2010-02-24
My routers are standard and cheap routers :p. I was thinking about the 2nd option configuring the NAT of the router. Do you know where I could find the info to create the proper config files for the OpenVPN client and server?

Thanks

---

### Post by dvlchd3 on 2010-02-24
This should get you started.  I have never actually set this up before, however, I have maintained networks that have had this kind of bridged connection.  As always, if you get stuck someplace, the whole community is here to help :)

This is just a part of the OpenVPN howto, you will notice at the end it says "continue where you left off in the HOWTO".  Therefore, my suggestion, study this part (since it is essential to your setup), then follow the HowTo from start to where it talks about Ethernet bridging (in Creating Config files for servers and clients), follow this part of the HowTo, then follow the rest of the HowTo.

[http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html)

Also, the documentation on the Ubuntu Help site may help as well:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

This will show any particulars to setting up OpenVPN and configuring it specifically for Ubuntu.

All in all, this is not going to be a simple process, and probably rather time-consuming.  Just keep this in mind. :)

---

### Post by mosquetero on 2010-02-24
Thank you so much!

I am reading it and I don't get any error while executing the scripts. When the OpenVPN is started, everything goes smoothly and when the client (PC in LAN2) is connected, it gets a correct IP address within LAN 1. However, I cannot ping from the client to any of the computers in my LAN 1 :(.

To be more precise, my server IP address is 192.168.1.101 and the VPN client address pool is 192.168.1.128 -- 192.168.1.254. The client in LAN2 gets the address 192.168.1.128 from OpenVPN but then I can't ping 192.168.1.101 or 102 (which is another PC). However, I can ping 192.168.1.1 which is nothing since the router is in the address 100. Any idea??

Thank you

---

### Post by dvlchd3 on 2010-02-24
From: [http://openvpn.net/index.php/open-source/faq.html](http://openvpn.net/index.php/open-source/faq.html)

> 
My OpenVPN client and server say "Connection Initiated with x.x.x.x" but I cannot ping the server through the VPN. Why?
This usually occurs because a firewall on the server or client is blocking the TUN/TAP interface. If you already have a firewall on your system, chances are high that it will block incoming connections on new interfaces by default, so you will need to add explicit firewall rules to allow connections via the TUN/TAP interface. In general, it's reasonable to open up TUN/TAP interfaces to all traffic, since any incoming connections over these interfaces will already have been authenticated by OpenVPN. An exception to this rule would be if you don't fully trust the OpenVPN clients connecting to the server. Assuming that's not the case, on Linux, TUN/TAP interfaces can be opened up with the iptables shell command:

# Allow TUN interface connections to OpenVPN server
iptables -A INPUT -i tun+ -j ACCEPT
# Allow TUN interface connections to be forwarded through other interfaces
iptables -A FORWARD -i tun+ -j ACCEPT 
# Allow TAP interface connections to OpenVPN server
iptables -A INPUT -i tap+ -j ACCEPT 
# Allow TAP interface connections to be forwarded through other interfaces
iptables -A FORWARD -i tap+ -j ACCEPT

On Windows XP, the firewall can be accessed by Control Panel -> Security Center -> Windows Firewall -> Advanced. In the Network Connection Settings control, uncheck the box corresponding to the TAP-Win32 adapter.

Note that if you want OpenVPN clients to be able access other machines on the LAN, it is not enough to merely disable firewalling on the TUN/TAP adapter. You must also enable IP forwarding and set up a return route from the LAN gateway to the OpenVPN server. This is discussed at length in the HOWTO.

Also note that firewalling the TUN/TAP interface is a completely separate operation from firewalling the internet-facing interface. For example, suppose an OpenVPN client is sending email via SMTP over the OpenVPN tunnel. The OpenVPN server firewall will need to allow both incoming encrypted data on TCP/UDP port 1194 via the internet-facing interface as well as incoming SMTP connections via the TUN/TAP interface.

---

### Post by mosquetero on 2010-02-24
I know what was happening, I tell you: My server is in a laptop. The router using a NAT forwards the OpenVPN petitions to my laptop over WIFI. Besides, my laptop is connected with all the other devices with WIFI too. Therefore, if I am correct, in the script bridge-start of the tutorial, I should write eth="wlan0" instead of eth="eth0" but in that case I stop having WIFI when I start the bridge and thus I can't receive the OpenVPN petitions from the client. Any idea??

THanks

---

### Post by mosquetero on 2010-02-25
Ok, finally I managed to find a partial solution, it is not exactly what I wanted but it's not far away.

I wanted:  

client ====VPNTUNNEL====== server (connected to router and LAN using eth0)

I get

client ====VPNTUNNEL====== server (connected to router using wlan0 and LAN using eth1).

Since I wanted the client to see the LAN, the solution I got is enough for me. If someone is interested in doing it, just follow [http://openvpn.net/index.php/open-so...-bridging.html](http://openvpn.net/index.php/open-so...-bridging.html) with few changes.

First change:

add the commands 
```

iptables -A INPUT -i tap0 -j ACCEPT
iptables -A INPUT -i br0 -j ACCEPT
iptables -A FORWARD -i br0 -j ACCEPT
```

to the bridge-start script.

In the server.conf: 

type local 192.168.2.2 (your IP in wlan0, exactly where you have configured the listener of the OpenVPN port in the NAT).

and server-bridge 10.1.0.1 255.255.255.0 10.1.0.10 10.1.0.20

10.1.0.1 --> Ip address of the server in LAN (eth1)
255.255.255.0 --> NetMask

10.1.0.10/10.1.0.20 IP range that the clients will get.

Hope I help!

---

