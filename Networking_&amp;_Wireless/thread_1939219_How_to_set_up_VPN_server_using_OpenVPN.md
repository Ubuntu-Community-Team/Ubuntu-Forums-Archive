---
title: "How to set up VPN server using OpenVPN"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Woohooo on 2012-03-11
Hi all,

I am trying to set up a VPN server using Open VPN. I followed all the instructions here:

[https://help.ubuntu.com/community/OpenVPN#Other_Resources](https://help.ubuntu.com/community/OpenVPN#Other_Resources)

All seems to go well and I get no errors while running any of the commands. Info which may be useful:


[LIST]
[*]I have a Netgear router and connect to it (and access the web) via a wireless network card which is identified as wlan1
[*]Trying to follow the instructions in the link the best I could, my /etc/network/interfaces file is as follows:
[/LIST]
[INDENT]> auto lo br0

iface lo inet loopback

iface br0 inet static
  address 192.168.1.33
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports wlan1

iface wlan1 inet manual
 up ip link set $IFACE up promisc on
 down ip link set $IFACE down promisc off[/INDENT]
[LIST]
[*]My static IP is therefore 192.168.1.33
[/LIST]
I have generated all the keys and basically got to the point where clients should be able to connect, restarted my computer. I then have no wireless connectivity whatsoever... I have to change the above file back to what it was before to get the net back so I can type this. As well as that, I think there may be a problem with my server.conf file. Here it is: 



> mode server
tls-server

**local <your.ip.addres.here> ## ip/hostname of server**
port 1194 ## default openvpn port
proto udp

#bridging directive
dev tap0 ## If you need multiple tap devices, add them here
up "/etc/openvpn/up.sh br0 tap0 1500"
down "/etc/openvpn/down.sh br0 tap0"

persist-key
persist-tun

#certificates and encryption
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
tls-auth ta.key 0 # This file is secret

cipher BF-CBC        # Blowfish (default)
comp-lzo

#DHCP Information
ifconfig-pool-persist ipp.txt
**server-bridge 192.168.1.33 255.255.255.0 192.168.1.100 192.168.1.110**
[B]push "dhcp-option DNS your.dns.ip.here"
push "dhcp-option DOMAIN yourdomain.com"[/B]
max-clients 10 ## set this to the max number of clients that should be connected at a time

#log and security
user nobody
group nogroup
keepalive 10 120
status openvpn-status.log
verb 3I have made bold several lines. It is these I am unsure how to configure. On the first bolded line, which IP do I put? 192.168.1.33? And do I leave the <> or is that just an indicator as used in documentation and I should type the IP only?



On the next bolded line I have as you can see replaced 192.168.1.10 with my static IP. The next address is the subnet mask. I don't understand what the next two addresses refer to. Is one of them supposed to be the gateway? Mine is 192.168.1.1.


One of them being the gateway makes sense, but which one? And why is there a fourth ... and what does it refer to?


Sorry for the epic post and many questions. Thank you in advance for reading and for any help you can provide - it is much appreciated.

---

### Post by Woohooo on 2012-03-12
Any ideas anyone? Presumably someone has done this before... It really should be quite simple. Ubuntu 11.10, connect to web through wireless, want to set up VPN so I can access my internet connection from other locations.

 :cry:

If there is another way (other than OpenVPN), please point me to it.

---

### Post by Woohooo on 2012-03-14
Hi all,

I have scrapped the OpenVPN idea as I cannot get it to work on my own. I have however set up a pptpd VPN server successfully using this guide:

[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

All is well. However I now need to know how to connect to my server from a remote location on a Windows 7 machine. How is this done?

This being a Linux forum I do not expect any of you to know the ins-and-outs of using the Windows interface, but what is required must be similar to what is required for any other OS. In Ubuntu I need:

Gateway:
Username:
Password:
NT Domain:

Usernames and passwords I have because I defined them. ;) But what would I enter in Gateway? My external IP address? And what about NT domain? IPv4 settings I think I understand: I would enter one of the addresses in the range I allowed when configuring the server.

Help would be appreciated greatly as I *have* to get this working.

---

### Post by heihaha on 2012-03-15
how to set up pptp?

---

### Post by Woohooo on 2012-03-15
I think I am nearly there with this. When I have successfully connected to my server from a remote machine I will post a step-by-step guide on a new thread...

---

### Post by heihaha on 2012-03-23
pptp or l2tp

---

### Post by RyanRahl on 2012-03-23
you need to add your tun/tap interface (respectively) to your Ethernet bridge. You only have the wlan1 in your br0. plus you are supposed to use a hyphen, not an underscore. try this in your interfaces file

```
# The local network interface
auto br0
iface br0 inet static
address         192.168.1.33
network         192.168.1.0
netmask         255.255.255.0
broadcast       192.168.1.255
gateway		192.168.1.1
bridge-ports    wlan1 tap0

# WiFi Interface
auto eth0
iface eth0 inet manual

# VPN Tap Interface
auto tap0
iface tap0 inet manual
```

You shouldn't need any of that promiscuous mode stuff unless you are trying to make it a wireless access point. Allow me to also suggest that you use a less common subnet because it will confuse the routing of your clients if they connect from a network that also has the same subnet, in your case 192.168.1.0/24. Try 192.168.194.0/24 or something. See how far this gets you and post back, I set these OpenVPNs up all the time.

Also, you are better off using the documentation here:
[http://openvpn.net/index.php/open-source/documentation.html](http://openvpn.net/index.php/open-source/documentation.html)

---

### Post by RyanRahl on 2012-03-23
Try this for your server config

```

port 1194
proto udp
dev tap0
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.33 255.255.255.0 192.168.1.150 192.168.1.200
server-bridge
client-to-client
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 4

```

This is a config file from a working server [slightly modified for your IP subnet]

---

### Post by Woohooo on 2012-03-30
Apologies, [RyanRahl]("http://ubuntuforums.org/member.php?u=1035437"), I did actually get the server up and running and I did not see your post. Thank you for replying though. 

Unfortunately I have been so busy working I have not had time to post the step-by-step guide as promised, or even look at the forums. 

I suspect your posts would have helped me but I still don't have time to go though it all and write up the the guide - I will when have time. I just wanted to thank you and everyone else for their input whether I used it or not. Your time and effort is much appreciated.

---

### Post by soniax on 2012-07-09
This article helped me a lot with the same issue:
[http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu/](http://www.ventanazul.com/webzine/articles/openvpn-ubuntu-and-hulu/)[]("http://www.superbvpn.com/vpn-uk")

I use [uk vpn service]("http://www.superbvpn.com/vpn-uk") for BBC iPlayer and everything works great.

---

