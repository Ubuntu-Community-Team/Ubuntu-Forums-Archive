---
title: "Configuring Laptop as a Router for XBox360"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by boaty on 2009-11-29
Hey everyone, I just bought a 360 today (Yay me!), but I need to find a way to bridge the connection between my xbox and my laptop (running ubuntu 9.04).  I've worked through a [tutorial]("http://www.linuxquestions.org/linux/answers/Networking/Connecting_to_XBox_Live_through_a_linux_computer_connected_to_a_wireless_LAN"), and this is what I've typed in:
```

ifconfig eth0 up
ifconfig eth0 192.168.2.1
echo "1" > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.2.0/24 -j MASQUERADE
iptables -t nat -A PREROUTING -i wlan0 -p tcp --dport 3074 -j DNAT --to-destination 192.168.2.1
iptables -t nat -A PREROUTING -i wlan0 -p udp -m multiport --dports 88,3074 -j DNAT --to-destination 192.168.2.1
iptables -A FORWARD -i wlan0 -d 192.168.2.1 -p tcp --dport 3074 -j ACCEPT
iptables -A FORWARD -i wlan0 -d 192.168.2.1 -p udp -m multiport --dports 88,3074 -j ACCEPT

```

Note:  The last four lines, I've used 192.168.2.0 and 192.168.2.2 as the IP.  None of those IPs do anything different (as far as connecting to the internet goes).

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:03:25:52:de:38  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe52:de38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2454 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152340 (152.3 KB)  TX bytes:7835 (7.8 KB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18456 (18.4 KB)  TX bytes:18456 (18.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:f7:95:72  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fef7:9572/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26367 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17089317 (17.0 MB)  TX bytes:6384590 (6.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-F7-95-72-35-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

These are my current XBox Network Settings:
```

IP Settings:  Manual
IP Address:  192.168.2.2
Subnet Mask:  255.255.255.0
Gateway:  192.168.2.1

DNS Settings:  Manual
Primary DNS Server:  72.160.197.212
Secondary DNS Server:  0.0.0.0

```

The external IP report to me by [http://www.myrouterip.com/](http://www.myrouterip.com/) is:
```

72.160.197.212

```

So, I hope I have everything up there...Can you guys help me out, I'm really at a loss here (I've been at this for the last couple of hours)

Edit:
Previous to Agent ME's suggestion, I was able to connect to the network, but not the internet.
Now, I can't connect to the network at all.
I'm going to try to reverse it and see what happens.
Edit 2:
I redid my steps that I posted above and can now again connect to the network...now just for the internet...

---

### Post by Agent ME on 2009-11-29
I've used NetworkManager's internet connection sharing feature so I could connect my xbox 360 to my laptop's ethernet port, and my laptop was connecting to wifi. You can set this up by right-clicking NetworkManager's icon, Edit Connections..., Wired, select auto eth0, Edit..., IPv4 Settings, and set Method to "Shared to Other Computers".

However, this doesn't let the xbox forward it's ports, so it will report itself as being under a "Medium" (or "Closed", can't remember) NAT.
(Xbox under open NAT can connect to anyone; People under medium NAT can't directly connect to people under closed NAT; closed NAT can only directly connect to people under open NAT.)

---

### Post by boaty on 2009-11-29
Well, when I did that, it stopped connecting to the network (instead of just connecting to the network and failing on the internet)

Any other ideas?

Edit:

I'm still looking for a solution; any help or insight would be appreciated.

---

### Post by boaty on 2009-11-30
I really need some help now.  I'm almost positive the problem is with my laptop, not the xbox.  I have all the network settings on the xbox correct; I'm sure of that.

Something must be missing here...has no one else done this before?

---

### Post by purct on 2009-11-30
after a quick read of your post, it appears that you have configured the Primary DNS Server(on your xbox) as your DNS.  I suspect thats your problem...your wireless router is unlikely to resolve DNS when its being addressed using your routers external interface. 

Try changing DNS addresses to match the ones in your /etc/resolv.conf file.  

or you could try OpenDNS Addresses:

208.67.222.222 
208.67.220.220

---

### Post by boaty on 2009-11-30
purct...I love you.  That is no joke.  I will always remember you...

:P

Seriously though, thanks a ton man.  You are a great person.  I opened up my /etc/resolv.conf and used that IP.  Worked like a charm.

I would also like to through out a big thanks to anyone who tried aiding me in this :D

---

### Post by Akoi Meexx on 2010-01-15
Thanks for the pointer in using /etc/resolv.conf for the ip addresses I needed, Purct! Got Moderate Connection available via Network Manager -> Auto Eth0 -> IPv4 -> Share this connection; then adding in the ip addresses into the network connection information on the 360.

Anyone know of how to make the connection open, instead of moderate?

---

