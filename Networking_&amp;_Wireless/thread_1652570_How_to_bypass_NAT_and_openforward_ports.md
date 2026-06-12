---
title: "How to bypass NAT and open/forward ports"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by prat22 on 2010-12-25
[B]Hi, 

What I am trying to do is, download torrents!!:p

I am using a BSNL 3G wireless internet connection, and I am unable to download torrents at horrible speeds of <1kbps...

What I found out is my comp is behind a Router, which acts as a NAT ( Network address translator). It connects to me (and several others using this service) as a local network, and connects to the internet using a public IP. Hence, all subscribers are connected to the internet via a single IP. This makes downloads from file hosting sites such as rapidshare almost impossible, since they think that my IP is already downloading a file (Though it traces the external public ip of my ISP router, and not my comp's original IP within the private network)!

However, I am using leech sites for this purpose.;)

But, torrent downloading is a problem now. It seems my downloader is not getting any incoming connections. (uTorrent via Wine shows this error).

My ifconfig results are:
[/B]
eth0      Link encap:Ethernet  HWaddr 00:23:5a:f1:60:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262283 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13152473 (13.1 MB)  TX bytes:13152473 (13.1 MB)

[B]ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.68.24.148  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:789400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1068158473 (1.0 GB)  TX bytes:38357155 (38.3 MB)[/B]

wlan0     Link encap:Ethernet  HWaddr 00:25:56:a6:0e:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[B]

I did nslookup google and it gave me:

[/B]$ nslookup [www.google.com]("http://www.google.com")
Server:        4.2.2.1
Address:    4.2.2.1#53

Non-authoritative answer:
[www.google.com]("http://www.google.com")    canonical name = [www.l.google.com]("http://www.l.google.com").
Name:    [www.l.google.com]("http://www.l.google.com")
Address: 66.102.7.104
Name:    [www.l.google.com]("http://www.l.google.com")
Address: 66.102.7.99[B]

When I go to sites which displays my IP, they show my IP is [/B]218.248.80.53, [B]which is probably the public (external) IP of my ISP's router!!

So, I need to forward a port to uTorrent, so that it can download through it!

Any Ideas???

Note: I dont know the model/make of my ISP's router!!

[/B]

---

### Post by ottosykora on 2010-12-26
you cant do anything about the ISP equipment at all. This is a proxy, they have to use it this way.
They can also block singl services if they like. Some will allow many things but no ftp for example, other will block any attampts to use VOIP etc.

First: try with normal torrent , I think the normal bittorrent is installe by default in ubuntu.
If it fails then it does not work, you can not do anything about it unless you build up a vpn to some other server under your control and start the service from there.

---

### Post by prat22 on 2010-12-26
Thanks a lot!! 

The default torrent downloader doesnt work either!

Do you think some kind of reverse tunneling can work? 

Can you guide me to set up a VPN? I dont have a router.

---

### Post by ottosykora on 2010-12-26
>Do you think some kind of reverse tunneling can work?<

have so far not heard about anything like that

>Can you guide me to set up a VPN? I dont have a router.<

start VPN to where? For that , you need a server, where VPN is running and is expecting your VPN calls and where also the software is running you want to use (torrent) and will also pass all the traffic via the tunnel back to your computer.

So best organize yourself a server with fixed IP from a reliable provider who does not block torrent. Connect it to net and then start thinking about VPN to it etc.

VPN is a two parts component, client and server. To have only one is pointless. 

You may also google little bit , there are some commercial companies which will for some fee provide you the other end of the VPN line. What additional services or what servie forwarding they will provide depends on the company aim.

You simply can not do what you want with the provider you have. Give it up.

---

### Post by prat22 on 2010-12-27
Thanks for clarifying me!! Let me see what I can do!!

---

