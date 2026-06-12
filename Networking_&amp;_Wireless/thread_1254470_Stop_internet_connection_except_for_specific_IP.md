---
title: "Stop internet connection except for specific IP"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2009-08-31
I'm trying to get VPN working on my computer and one thing that I would like to fix is that if I get disconnected from the VPN wont the computer connect to the internet. I'm unsure on how to fix this one possible way would be to block all outgoing and incoming traffic in iptables except for those IP address that are allowed, but I'm unsure how to do this?

---

### Post by Iowan on 2009-08-31
*Sounds* like something that would be set in the router/firewall.

---

### Post by SpinningAround on 2009-09-01
below

---

### Post by SpinningAround on 2009-09-02
Well I have tried to get the VPN working but I can't connect for some reason and I haven't figured out why, this is how it look atm it's something that I have left out that cause the failure to connect 
```

sudo iptables -F
sudo iptables -X
#
sudo iptables -A OUTPUT -d 80.67.2.66  -j ACCEPT
sudo iptables -A OUTPUT -d 80.67.2.67  -j ACCEPT
sudo iptables -A OUTPUT -d 80.67.2.68  -j ACCEPT
sudo iptables -A INPUT -d 80.67.2.66  -j ACCEPT
sudo iptables -A INPUT -d 80.67.2.67  -j ACCEPT
sudo iptables -A INPUT -d 80.67.2.68  -j ACCEPT
#
sudo iptables -A INPUT -p udp -m udp --sport 53 -m state --state ESTABLISHED -j ACCEPT 
sudo iptables -A OUTPUT -p udp -m udp --dport 53 -j ACCEPT 
sudo iptables -A INPUT -p tcp -m tcp --sport 53 -m state --state ESTABLISHED -j ACCEPT 
sudo iptables -A OUTPUT -p tcp -m tcp --dport 53 -j ACCEPT
#
sudo iptables -A OUTPUT -p tcp -m tcp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p udp -m udp --dport 1723 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A INPUT -p tcp -m tcp --sport 1723 -m state --state ESTABLISHED -j ACCEPT
sudo iptables -A INPUT -p udp -m udp --sport 1723 -m state --state ESTABLISHED -j ACCEPT
#
sudo iptables -A OUTPUT -p udp -m udp --dport 67 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -P FORWARD DROP

```
log error
```

nm-pptp-service-12865 log[ctrlp_disp:pptp_ctrl.c:929]: Call disconnect notification received (call id 20899)
pppd[12868]: LCP: timeout sending Config-Requests 
pppd[12868]: Connection terminated.
NetworkManager: <info>  VPN plugin failed: 1 
pppd[12868]: Modem hangup
pptp[12872]: nm-pptp-service-12865 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
pptp[12872]: nm-pptp-service-12865 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
pptp[12880]: nm-pptp-service-12865 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
pptp[12880]: nm-pptp-service-12865 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
pptp[12880]: nm-pptp-service-12865 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
pppd[12868]: Exit.
NetworkManager: <info>  VPN plugin failed: 1 
NetworkManager: <info>  VPN plugin state changed: 6 
NetworkManager: <info>  VPN plugin state change reason: 0 
NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.

```

---

### Post by denver on 2009-09-02
Iptables firewall rules are first hit, not best fit. That means that if a packet matches the first rule, the rest of the rules are not checked any more.

I see that your first 3 rules all drop packets. Thats not wise, as you basically stop ALL traffic comming in and going out on all interfaces. Generic DROP rules should be placed at the END of the firewall rule set.

If you really want to use firewall rules you can use something allong the lines of:

```
iptables -I OUTPUT -p tcp -o ! vpn0 -j DROP
iptables -I INPUT -p tcp -i ! vpn0 -j DROP

```

But i am not 100% sure it would work.

These 2 rules will drop all pachets in and out that are not routed through vpn0 (your VPN interface). Please make sure that vpn0 is the interface used for a default route. You should be able to find out if this is the case by running:

```
 
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
80.96.84.0      0.0.0.0         255.255.255.128 U     2      0        0 wlan0
0.0.0.0         80.96.84.1      0.0.0.0         UG    0      0        0 wlan0

```

In my case wlan0 is the interface used as default route.

If all you want to do is route all traffic through your VPN connection and nothing else, this can be done via static routes. However, all static routes should be defined in nm-applet to avoid loosing them every time you disconnect from the VPN.

Would help to know a bit about your network layout but i'll just try and give you a model bassed on a generic SOHO (Small Office/ Home Office).

Let's say you have an access point that you use to connect to the internet (192.168.0.1). Let's also assume that your VPN service gateway (the server you authenticate to) is 10.0.0.1.

Normally, you would use 192.168.0.1 as your default gateway and route all traffic through that. To avoid that and STILL be able to connect to 10.0.0.1 we will have to create a static route to that host.

Right click on nm-applet and go to edit connections. Select your connection (eth0/wlan0 or whatever) and hit EDIT. Go to IPv4 settings and select as "Method": Manual.

Next to "Address" you have an "Add" button. You will need to add an IP address for this connection and a Netmask but NOT, i repeat NOT a Gateway.

Your address should be something like 192.168.0.100 and your netmask should be 255.255.255.0. As a DNS server you should use your ISP's DNS servers or OpenDNS...or whatever rocks your boat.

Now, we have set an IP address and a netmask, but because we don't have a Gateway, we will NOT be able to access the internet or the VPN service. To be able to connect to the VPN service we will add a static route.

Just hit the "Routes" button at the bottom of the "IPv4 settings window" and hit "Add".

You will need to add 10.0.0.1 (address), 255.255.255.255 (Netmask), 192.168.0.1 (Gateway <-- this is your AP). This is a host only route, it tells your computer how to reach only this host (10.0.0.1).

You will now be able to connect to your VPN provider and route all traffic through it. If your VPN fails, you will loose all connectivity to the internet, except for 10.0.0.1.

If you decide you need network conectivity the old fassion way, just add a gateway in the "Address" field for your connection. When the VPN fails, all traffic will be routed through your normal connection.

Good Luck!

---

### Post by SpinningAround on 2009-09-02
Thanks for the reply, I think it almost worked but something I noticed when using your guide was that I probably isn't on a SOHO, while checking the logs simply to understand what was happening did the computer first get a IP, gateway, subnet from a DHCPserver then later it got my actual network info. I guess that it's something like this

--INTERNET--> >--BIG NETWORK--> >--"SMALL" NETWORK--> >--MY COMPUTER-->

This is what I see
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
then later
<info>    prefix 23 (255.255.254.0)

---

### Post by denver on 2009-09-02
```
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
```

Thats a DHCP discover packet. Its ment to find a DHCP server on a network, from which to request network information (IP, Gateway, netmask, DNS server, etc). You should later see a DHCPREQUEST and DHCPACK packet if i remember correctly. Your ISP must be issuing you an IP address via DHCP. 

Also, you would know if you had a SOHO type network. They usually imply a personal access point wich shares internet to multiple PC's in your office or home.

If your ISP gives you the same network information every time, the guide should still work, just use your network info statically. It could however be problematic if your ISP decides to change your IP.

Im sorry i can't be of much use when it comes to complex firewall rules. In any case, good luck!

---

### Post by SpinningAround on 2009-09-09
I tried but didn't succeed but I found out what ip there servers use and what IP they then give to they who connect. 

They use the following for authentication / login server
80.67.2.66
80.67.2.67
80.67.2.68

Then they give does that connect through them any of the following.
80.67.10.0 -> 80.67.15.255

Should this info be set up in some sort of order?
Should all 80.67.10.0 -> 80.67.15.255 be added to routes or only login server?

---

### Post by SpinningAround on 2009-09-13
Almost have it solved now, I added dns server to route and this solve the problem with host not found for vpn.anonine.net yet there is one thing that is still missing, when I get connected to the VPN do I get a "new IP" it looks like this is why I can't connect to the internet yet.

---

