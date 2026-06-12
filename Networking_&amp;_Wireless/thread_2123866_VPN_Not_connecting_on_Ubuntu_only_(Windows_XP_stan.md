---
title: "VPN Not connecting on Ubuntu only (Windows XP standard openVPN client works)"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by svaens on 2013-03-09
Hi all, 

The title says it all. 

Recently It has been impossible to connect to my VPN Service. 
I had initially thought it was a problem of the service, 
however, having checked the possibility to connect, using the open source openVPN client for windows XP, and seeing it works without hesitation, 
obviously it is more related to Ubuntu. 

The error I get (from command line.... it also does not work by GUI clicking anymore....) is the following:

xxx@svUbuntu10:~$ nmcli con up id VPNService
Active connection state: unknown
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/8
state: VPN connecting (need authentication) (2)
state: VPN connecting (3)
state: VPN connecting (getting IP configuration) (4)
Error: Connection activation failed: the connection attempt timed out.
xxx@svUbuntu10:~$ 

Has anyone any idea why this might be the case?

I am currently on ubuntu 12.04, latest updates as of march 2013. 

thanks in advance for any help.

---

### Post by svaens on 2013-03-09
Update:

I am able to create an openvpn connection still via command line ... invoking 'openvpn' with the correct argumnts. 
This would be a temporary (but unsatisfacty .... one more damn thing in ubuntu broken that used to work) solution, 
except, 
where as before the network manager solution broke, I had no dns leaks, 
with the command line solution, I do. 

anyone ?

---

### Post by svaens on 2013-03-11
ahh, still no reply.
This forum is about as helpful as a kick in the head. 

Nonetheless, 

I must report that I have worked around my problems. 

Accepting that the Network Manager is broken, and despite this being a LTS, ain't gonna be fixed any time soon, i've resorted to invoking the openvpn command directly. 

```
sudo openvpn --client --config /home/xxx/bin/vpn/config/vpn.ovpn --ca /home/xxx/bin/vpn/config/vpn.ca.crt
```

My next problem to solve is preventing dns leak. 

I had thought to do this via some rules appended to ufw, using the iptables command. 
It is fairly complicated, and i'm simply not yet up to the task. But I will continue to learn it, as it is definitely a good thing to understand it.
However, I came across a post by someone which suggested I add some lines to my VPN configuration file. 

I also don't understand those lines, though I will (when I get time) research it.
Unless it is a freak coincidence, it seems to have done the trick.

I prepended the following lines to the vpn.ovpn file:

```
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
script-security 2
```

Additionally:
I was setting this up on debian just now, and it wouldn't work. 
It seems I came across a problem that one would also see on Ubuntu. 

Apart from prepending the following lines to the vpn.ovpn file:

Code:

```
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
script-security 2
```

I needed to make sure I had installed **resolvconf** (otherwise I still got a DNS leak).
i.e., 
```
sudo apt-get install resolvconf
```

and no, that is not a typo. It is 'resolvconf' not 'resolveconf' which I first accidentally attempted to install. 

Now no dns leak. 
[http://www.subvs.co.uk/openvpn_resolvconf](http://www.subvs.co.uk/openvpn_resolvconf)
[https://forum.perfect-privacy.com/showthread.php?t=1823](https://forum.perfect-privacy.com/showthread.php?t=1823)
[http://askubuntu.com/questions/229041/connect-only-via-vpn](http://askubuntu.com/questions/229041/connect-only-via-vpn)

I also apply some firewall rules which at least prevent non-dns traffic going out should the VPN drop out. 

"Assumptions: you are in a 192.168.0.0/16 network and your router is a DHCP server. You have a a physical network interface named eth*. The tun adapter is tun* and the loopback interface is lo."
[https://airvpn.org/index.php?option=com_kunena&func=view&catid=3&id=1713&limit=6&limitstart=30&Itemid=142#2010](https://airvpn.org/index.php?option=com_kunena&func=view&catid=3&id=1713&limit=6&limitstart=30&Itemid=142#2010)

```
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT #allow loopback access
iptables -A OUTPUT -d 255.255.255.255 -j  ACCEPT #make sure you can communicate with any DHCP server
iptables -A INPUT -s 255.255.255.255 -j ACCEPT #make sure you can communicate with any DHCP server
iptables -A INPUT -s 192.168.0.0/16 -d 192.168.0.0/16 -j ACCEPT #make sure that you can communicate within your own network
iptables -A OUTPUT -s 192.168.0.0/16 -d 192.168.0.0/16 -j ACCEPT
iptables -A FORWARD -i eth+ -o tun+ -j ACCEPT 
iptables -A FORWARD -i tun+ -o eth+ -j ACCEPT # make sure that eth+ and tun+ can communicate
iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE # in the POSTROUTING chain of the NAT table, map the tun+ interface outgoing packet IP address, cease examining rules and let the header be modified, so that we don't have to worry about ports or any other issue - please check this rule with care if you have already a NAT table in your chain
iptables -A OUTPUT -o eth+ ! -d a.b.c.d -j DROP  # if destination for outgoing packet on eth+ is NOT a.b.c.d, drop the packet, so that nothing leaks if VPN disconnects
```

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

In looking up all the various pages that helped me, and dumping them here (for your convenience) I came across more
Amazing how easy the stuff is to find, once you have the right search strings. But in searching simply for 'dns leak vpn ubuntu or linux', or variations of that, It took a while to find anything that helped me. 

Anyway, hopefully, if someone comes across this, having the same problem as I have, they find it helpful.

---

