---
title: "server installation problems please help thanks"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by rsainath on 2009-06-16
At one time this desktop had ubuntu gui with underlying ubuntu server. Followed the steps given in the website [http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/) . Tried to add the website to the webserver with above ip address. Tested it from another Windows desktop using WinSCP but not able to connect to the server.Originally, I did the basic install of the ubuntu 8 server with xubuntu gui. Also installed Apache, MySQL, and PHP. Networked to three other Windows based desktops via Airlink 101 router ip address 192.168.1.10 (I don't use the wireless just the wired inputs). Also established a host at no-ip.org called iytherapy which makes the full name iytherapy.no-ip.org with ip address 192.168.1.102 (AND I STILL HAVE THIS).  After a few frustrating attempts I did a COMPLETE reinstall of the server but this time decided (for a change) to use xubuntu 8.xx. Did a complete basic install and here's the rest of what's going on and request any assistance to solve what seems to be a simple but elusive problem. Thanks people so here's where I have gotten so far after the new install:

Ran some test commands on the terminal as follows:
1. rsainath@iytherapy:~$ ifconfig
GETTING THE FOLLOWING RESPONSE:

ath0      Link encap:Ethernet  HWaddr 00:1d:6a:12:1d:e9  
          inet6 addr: fe80::21d:6aff:fe12:1de9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:0c:76:57:9b:65  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe57:9b65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3288431 (3.1 MB)  TX bytes:673555 (657.7 KB)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11676 (11.4 KB)  TX bytes:11676 (11.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1D-6A-12-1D-E9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17186 errors:0 dropped:0 overruns:0 frame:9877
          TX packets:321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1920908 (1.8 MB)  TX bytes:14766 (14.4 KB)
          Interrupt:21 

2. ifconfig | grep inet
GOT THE FOLLOWING RESPONSE:
rsainath@iytherapy:~$ ifconfig | grep inet
          inet6 addr: fe80::21d:6aff:fe12:1de9/64 Scope:Link
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe57:9b65/64 Scope:Link
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host

3. Tested on the web browser with the inet address 192.168.1.109 
GOT THE RESPONSE : "It works!"

4. Did a restart of apache2: sudo /etc/init.d/apache2 restart
GOT THE FOLLOWING RESPONSE:
rsainath@iytherapy:~$ sudo /etc/init.d/apache2 restart
[sudo] password for rsainath: 
 * Restarting web server apache2                                                
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

5. ping 192.168.1.109
PING 192.168.1.109 (192.168.1.109) 56(84) bytes of data.
64 bytes from 192.168.1.109: icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from 192.168.1.109: icmp_seq=2 ttl=64 time=0.045 ms
64 bytes from 192.168.1.109: icmp_seq=3 ttl=64 time=0.042 ms
64 bytes from 192.168.1.109: icmp_seq=4 ttl=64 time=0.045 ms
64 bytes from 192.168.1.109: icmp_seq=5 ttl=64 time=0.045 ms

--- 192.168.1.109 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 0.042/0.049/0.069/0.010 ms

6. Ping for my Airlink 101 router:
rsainath@iytherapy:~$ ping 192.168.1.10
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
64 bytes from 192.168.1.10: icmp_seq=1 ttl=64 time=1.13 ms
64 bytes from 192.168.1.10: icmp_seq=2 ttl=64 time=1.13 ms
64 bytes from 192.168.1.10: icmp_seq=3 ttl=64 time=0.982 ms
64 bytes from 192.168.1.10: icmp_seq=4 ttl=64 time=1.08 ms

--- 192.168.1.10 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.982/1.083/1.131/0.060 ms
rsainath@iytherapy:~$ 

7. ping 192.168.1.102 (that's the ip host address at iytherapy.no-ip.org. Not getting any response here's the ping results
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.

--- 192.168.1.102 ping statistics ---
39 packets transmitted, 0 received, 100% packet loss, time 38008ms

8. ping iytherapy.no-ip.org test results as below:
PING iytherapy.no-ip.org (76.167.70.6) 56(84) bytes of data.
64 bytes from cpe-76-167-70-6.socal.res.rr.com (76.167.70.6): icmp_seq=1 ttl=64 time=1.14 ms
64 bytes from cpe-76-167-70-6.socal.res.rr.com (76.167.70.6): icmp_seq=2 ttl=64 time=1.09 ms
64 bytes from cpe-76-167-70-6.socal.res.rr.com (76.167.70.6): icmp_seq=3 ttl=64 time=0.970 ms
64 bytes from cpe-76-167-70-6.socal.res.rr.com (76.167.70.6): icmp_seq=4 ttl=64 time=0.959 ms

--- iytherapy.no-ip.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.959/1.042/1.144/0.082 ms

9. Response to terminal query "hostname" is "iytherapy".


MY QUESTIONS:
1, What settings should I change (and in what files) to make this function properly ? 
2. What configuration changes should I make in the Airlink 101 router to make this work?
3. Port forwarding - not sure if I got this right. What SHOULD the settings be on the router and the appropriate desktop files?
4, Haven't added Website to Web Server - not sure what I should do until I figure out the rest of the stuff above.
5. Haven't installed any firewall as yet. Thought of installing shorewall with the settings indicated in the website "http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/" . Any firewall settings that would block server access?
FINAL COMMENTS: Been a great learning experience, feel better with each passing day, no substitute for hammering away at this till I get it to work.Would appreciate any comments with step-by-step on what changes I should make and where. 
THANKS PEOPLE AND FELLOW "UBUNTU"ANS !! I really appreciate it.

---

### Post by Iowan on 2009-06-16
The router has the address 192.168.1.10 ?
[This]("http://ubuntuforums.org/showpost.php?p=7311193&postcount=2") might help with the "apache2: Could not reliably determine ..." error.
I haven't (yet) used dyndns.com or no-ip.org, but it doesn't seem right to have a private IP address listed. 
Your server address (192.168.1.109) is static (not acquired via DHCP)? Your router should probably forward port 80 to 192.168.1.109. The router's external address is what I would expect to see linked to your iytherapy.no-ip.org name.

Hope I haven't added to confusion...

---

### Post by DGortze380 on 2009-06-16
> **rsainath said:**
> Also established a host at no-ip.org called iytherapy which makes the full name iytherapy.no-ip.org with ip address 192.168.1.102 (AND I STILL HAVE THIS).  

I haven't rea dyour whole post yet, but here's problem #1.
This is a reserved IP Address. It's not valid on the internet, it will not resolve, it's for your own use on your own network only.

Go to [http://www.whatsmyip.org/](http://www.whatsmyip.org/)
This is the address you need to associate with no-ip

---

