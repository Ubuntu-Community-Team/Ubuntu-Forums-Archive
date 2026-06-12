---
title: "Can't open a port for Transmission"
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by Ruzu on 2012-09-28
Hi, I spent the last few days wondering why Transmission can be so slow, before figuring out that the port it uses is closed. So I attempted to open it and spent literally half the night trying to do it. And I've read a lot of forum posts but as no solution presented there has worked for me, I have to ask for help myself.

Most answers were about forwarding ports in the router so I'm going to say right now, I think this is not the problem. I've had a lot of troubles with setting it up on Windows but eventually kind of got it going. Or at least BitTorrent was working great, because online games -- not so much. But I don't see why suddenly it wouldn't work at all on Linux. Anyway, my router is an ASUS RT-N11 and [COLOR=DarkOliveGreen][THIS]("http://imageshack.us/a/img268/2696/asusd.png")[/COLOR] is how it is forwarded. Now, I used a guide on [http://portforward.com/](http://portforward.com/) but, honestly, I'm like, 80% sure it works properly. Not entirely sure. But it doesn't matter because I temporarily turned the router's firewall off and it didn't change anything. On Windows this used to let me come around similar problems but not here.

Also my ISP doesn't block any ports.

System's firewall is disabled ("sudo ufw status" gives me "Status: inactive"). I installed Firestarter because of a suggestion on some forum, but it is disabled now, too.

"sudo netstat -ntlp" gives me:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1560/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1068/cupsd      
tcp        0      0 0.0.0.0:55000           0.0.0.0:*               LISTEN      2342/transmission-g
tcp        0      0 0.0.0.0:6881            0.0.0.0:*               LISTEN      2985/qbittorrent
tcp6       0      0 ::1:631                 :::*                    LISTEN      1068/cupsd      
tcp6       0      0 :::55000                :::*                    LISTEN      2342/transmission-g
tcp6       0      0 :::6881                 :::*                    LISTEN      2985/qbittorrent
```I have no idea what "netstat" actually does but I saw this somewhere.

"sudo iptables -L" gives a really weird output, as yesterday it was literally blank. It was just "Chain INPUT (policy DROP)", then nothing -- or my rule, after I put it in -- then "Chain FORWARD (policy DROP)" and so on.

Now it is, for some reason:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  localhost            anywhere             tcpflags:! FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  localhost            anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere             limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere             state INVALID
LSI        all  -f  anywhere             anywhere             limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level info prefix "Unknown Input"
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:55000

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere             limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level info prefix "Unknown Forward"
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:55000

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.210        localhost            tcp dpt:domain
ACCEPT     udp  --  192.168.1.210        localhost            udp dpt:domain
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere             state INVALID
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             LOG level info prefix "Unknown Output"
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:55000

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.214.216          anywhere            
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:55000
ACCEPT     udp  --  anywhere             anywhere             udp dpt:55000
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix "Inbound "
DROP       tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix "Inbound "
DROP       tcp  --  anywhere             anywhere             tcpflags: FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere             icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix "Inbound "
DROP       icmp --  anywhere             anywhere             icmp echo-request
LOG        all  --  anywhere             anywhere             limit: avg 5/sec burst 5 LOG level info prefix "Inbound "
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere             limit: avg 5/sec burst 5 LOG level info prefix "Outbound "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            

```Port 55000, which I chose for Transmission, is still closed when I test it on the [INTERNET]("http://imageshack.us/a/img607/1970/openporttest.png") and in [TRANSMISSION]("http://imageshack.us/a/img404/3729/transmission.png"). As you can see on the screenshot, uPnP is being used. It is also turned on on my router.

I use Ubuntu 12.04 and everything is updated. Transmission is version 2.61, as I updated it using their official ppa, in hope that it would help somehow. Transmission behaved the same way before the update.

So that's it. I wouldn't be surprised if by writing every command I found on the internet I screwed something and just made matters worse. But I hope something can still be done. I can't believe how hard it can be to just open one port.

PS. I don't know if prefix "ubuntu" for this thread was a good choice. Sorry if I made a mistake.

---

### Post by Ruzu on 2012-09-29
I guess my first post was a little "bloated" so I want to make things clear.

I flushed iptables and now they're empty. UFW has been reset and is disabled. There is no other firewall software. Router's firewall is temporarily disabled so it doesn't block anything at all. My ISP doesn't block anything. When Transmission is on, "netstat -ntlp" shows me that it listens to an appropriate port.

And yet Transmission, as well as [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/), tell me that the port is closed. [http://www.canyouseeme.org/](http://www.canyouseeme.org/) only says that it "could not see my service" because "connection timed out".

Curiously, "nmap 192.168.1.210 -p59654" tells me:
```
PORT      STATE SERVICE
59654/tcp open  unknown
```



Nevertheless torrents download at VERY low speeds. Uploading seems normal. Any suggestions?

---

### Post by houstonbofh on 2012-09-29
Saying "It works on Windows" is not an industry standard troubleshooting method.  The reason is that we do not know what random program did what to make it work.

So, to get to you on your port of choice, there needs to be a path to you.  Does your Linux box have a real IP, or is it NATed?  If NATed, you will need to forward that port to your system.  Windows may be doing that with UPNP or something similar depending on the client you are using.  From what you are showing, it is opne on your system, but not being seeing from the Internet.

---

### Post by Ruzu on 2012-10-05
By saying that it works on Windows, I just wanted to say that it probably isn't something with router or it's firewall because the only difference is the OS, not hardware configuration.

Sorry that my reply is so late but actually my router stopped working (I'm guessing something went wrong during firmware update I did) and I had some troubles connecting to the internet again. But now, at least, I can say that the situation is the same no matter whether I use router or connect directly.

Does my computer have a real IP, or is it NATed -- frankly, I'm not entirely sure. I have a local IP 192.168.1.101 -- and every computer in our network has a different one, ending with *.102 and *.103 -- as well as a different external IP. Does that mean that I'm using NAT? If so, then what do I have to do?

---

### Post by houstonbofh on 2012-10-07
Yes, you are using NAT.  And you need a path to you on the port you are using through the router giving you that IP address.  There are some UPNP ways to do this if your router supports it, and that may be what Windows was doing.

---

### Post by Ruzu on 2012-10-07
I have actually done this, both on the old router and on the new one that I bought recently.

[http://imageshack.us/a/img580/5053/pentagram.png](http://imageshack.us/a/img580/5053/pentagram.png)

I think this should work (I also assigned my computer's MAC address to the IP I used) but the port is still closed. My ISP said they don't block anything but is it possible that I can't connect through these ports because of something on their side?

PS. Also, my router supports uPnP and Transmission is supposedly using it. Is it something that doesn't exactly work on Ubuntu, or maybe requires some additional packages?

---

### Post by Superekian on 2012-11-12
Hello! Same problem, me too Ubuntu 12.04 LTS and one day spent reading  forum posts without any result: port still closed! Any suggestion?  Thanks! :smile:

---

