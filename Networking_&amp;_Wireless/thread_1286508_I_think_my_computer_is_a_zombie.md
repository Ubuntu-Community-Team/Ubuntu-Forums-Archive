---
title: "I think my computer is a zombie"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by mcp_ri on 2009-10-09
Recently I noticed a slight increase in my internet traffic so I started monitoring it. It appears that something is accessing internet even when I don't do anything on a computer. EtherApe shows a lot of packets being exchanged via UDP-unknown protocol with IP addresses which appear to be telecom companies (I used dnslookup). So, my opinion is that I have a program that DDoS that sites. How can I see which programs are using my internet connection? I tried Firestarter but it shows only my web browser, while it's obvious there are other programs. If you have a solution to this problem, I would be very thankful because I have a monthly limit on my internet traffic, so it's very important to me.

---

### Post by stinger30au on 2009-10-09
backup your email and other important data

format it and reinstall

piece of cake

oh yeah, and use a different password this time round

---

### Post by mcp_ri on 2009-10-09
Are you sure thats the only solution?
I don't feel like reinstaling everthing and setting up again.

---

### Post by callan79 on 2009-10-09
> **mcp_ri said:**
> How can I see which programs are using my internet connection?


Hi mcp_ri,

Go to a terminal, and use the netstat program. Type in

```
man netstat
```

for the full instructions, but for now you might just want to start with

```
sudo netstat -ap
```

Then (I think) you will see all the connections and which programs are using them.

Good luck!

Cheers
Callan

---

### Post by mcp_ri on 2009-10-09
here is an output I get after running:
```
sudo netstat -ape --inet
``````
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 localhost:32000         *:*                     LISTEN      milan      9171        3841/java       
tcp        0      0 localhost:mysql         *:*                     LISTEN      mysql      6465        2649/mysqld     
tcp        0      0 localhost:7634          *:*                     LISTEN      root       7128        3070/hddtemp    
tcp        0      0 localhost:ipp           *:*                     LISTEN      root       36366       3508/cupsd      
tcp        0      0 localhost:32000         localhost:31000         ESTABLISHED milan      10325       3837/wrapper-linux-
udp        0      0 acer-2sd.dum:netbios-ns *:*                                 root       608690      3139/nmbd       
udp        0      0 *:netbios-ns            *:*                                 root       7271        3139/nmbd       
udp        0      0 acer-2sd.du:netbios-dgm *:*                                 root       608691      3139/nmbd       
udp        0      0 *:netbios-dgm           *:*                                 root       7272        3139/nmbd       
udp        0      0 *:56852                 *:*                                 avahi      8515        3479/avahi-daemon: 
udp        0      0 *:bootpc                *:*                                 root       607440      16985/dhclient  
udp        0      0 *:mdns                  *:*                                 avahi      8514        3479/avahi-daemon: 
```non of them look suspicious to me.

however, etherape shows a lot of active connections as you can see in the attached screenshot.

---

### Post by callan79 on 2009-10-10
> **mcp_ri said:**
> however, etherape shows a lot of active connections as you can see in the attached screenshot.


Hi mcp_ri,

I wouldn't worry too much about it ... if netstat only shows valid connections you should be fine. But certainly that etherape stuff is a little weird.

Maybe try booting from a live CD and run etherape and see if you get similar results?

Else, can etherape tell you any more about the data? Like, is it definitely connected to your local IP, and which port?

---

### Post by mcp_ri on 2009-10-10
I managed to solve the problem! It was Freenet that sucked all my internet traffic. Anyway I removed that piece of crap from my laptop.

Thx everyone who tried to help me! :D

---

### Post by t0mppa on 2009-10-10
[Something]("http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/security-guide/s1-server-ports.html") I ran across the other day that might be of interest as well, particularly the part about:

> There are two basic approaches for listing the ports that are listening on the network. The less reliable approach is to query the network stack by typing commands such as netstat -an or lsof -i. This method is less reliable since these programs do not connect to the machine from the network, but rather check to see what is running on the system. For this reason, these applications are frequent targets for replacement by attackers. In this way, crackers attempt to cover their tracks if they open unauthorized network ports.

A more reliable way to check which ports are listening on the network is to use a port scanner such as nmap. 

---

