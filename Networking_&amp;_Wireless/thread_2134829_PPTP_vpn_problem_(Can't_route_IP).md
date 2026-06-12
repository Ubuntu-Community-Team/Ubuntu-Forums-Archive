---
title: "PPTP vpn problem (Can't route IP)"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by NovaDecker on 2013-04-12
Hi!
I am Norwegian, so if you dont understand what I'm writing here, so sorry my English.
Well, this is the case:
I have a server in Norway. This server does not have possibility to get static public IP-addresses, any way.
So I rent a server in NL with 4 static public IP-addresses.
I want to run PPTP VPN from NL to Norway, and route one of the public IP-addresses from NL to Norway.

Both servers run the lastest Ubuntu, 64 bits.

The NL public ip-addresses is (cencored of course):
xxx.xxx.xxx.146
xxx.xxx.xxx.147
xxx.xxx.xxx.148
xxx.xxx.xxx.149
The /etc/network/interfaces at the server in NL is set up with xxx.xxx.xxx.146 as main IP-address. I don't have set up the other IP-addresses in this file, because they have to be routed to Norway.

In my pptpd.conf file, I have:
localip xxx.xxx.xxx.146
remoteip xxx.xxx.xxx.146-149

And in my chap-secrets file I have:
Name server password ip like that:

Norway PPTP ****** xxx.xxx.xxx.147

When I connect, it works. I can connect the VPN-server.
But when I run this command:
ping -I ppp0 xxx.xxx.xxx.146
It works. I can ping the VPN-server.

If I run:
ping -I ppp0 google.com
It does NOT work. I can't ping other hosts.
I tried to run:
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
And set the ipv4_forward to 1. I checked with sysctl -p, and it outputs 1.

It didn't work either.

But when I connect from a Windows machine, it works. I can connect, I can ping any hosts, BUT:
My public IP-address is the same as the server's public IP, NOT the IP i have assigned.
(I can see in ipconfig that the VPN-server assigned xxx.xxx.xxx.147 to it, but when I go to whatismyip.com, it's xxx.xxx.xxx.146)

Well, I have given up.
Any solutions? What does I forgot?

Important note:
This worked before I reinstalled both servers...

---

### Post by NovaDecker on 2013-04-12
Half-solved:
If I does NOT make the firewall rule that masquerades eth0, it works on Windows.
Currently I have other problems with the ubuntu box, I will fix it and come back with feedback.

---

### Post by NovaDecker on 2013-04-13
Hi!
I'm back.
When I connect to the Ubuntu VPN server in Netherland from a Windows 7 machine (from same ISP), everything works. I can browse Internet, my IP is correct and everything.
But when I connect my Ubuntu server in Norway to the VPN-server, I get the IP-address, but it does not work.

Pinging VPN-server from the Ubuntu box in Norway, with interface ppp0 (where the VPN goes)
```

root@norwayserver:~# ping -I ppp0 xxx.xxx.xxx.146 (This is IP-address of VPN-server)
PING xxx.xxx.xxx.146 (xxx.xxx.xxx.146) from xxx.xxx.xxx.147 ppp0: 56(84) bytes of data.
--- xxx.xxx.xxx.146 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

```
Pinging ubuntuforums.org from the Ubuntu box in Norway, with interface ppp0 (where the VPN goes)

```

root@norwayserver:~# ping -I ppp0 ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) from xxx.xxx.xxx.147 ppp0: 56(84) bytes of data.
--- ubuntuforums.org ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

```

Pinging the Norway-server from VPN-server in NL:
```

root@vpn:~# ping -I ppp0 xxx.xxx.xxx.147
PING xxx.xxx.xxx.147 (xxx.xxx.xxx.147) from xxx.xxx.xxx.146 ppp0: 56(84) bytes of data.
--- xxx.xxx.xxx.147 ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms

```

I have enabled ipv4 forward in /etc/sysctl.conf at the VPN-server. As I said, everything works from Windows, but not from the Ubuntu server.
Any ideas?

---

