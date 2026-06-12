---
title: "Networking woes 9.04 64 bit"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by Skyleaper on 2009-09-27
Ok, I'm a bit of a n00b, but never really seen this behavior before. This problem is the same with either the realtek wired NIC in this laptop (HP dv5000) or the Broadcom wireless. Things worked swimmingly for about 3 weeks. Took the laptop out of the house to a coffee shop and searched for an access point there. There was none. So when I came home and fully expected the wireless to reconnect as it always has, it did, but, I can't do anything but ping addresses. The DHCP in the router has assigned the laptop an IP address, Shows both DNS name servers and the IP Hostname in nm-applet. As I stated, I can ping both the router and outside addresses, but it will not connect with anything else. I tried to connect with the Realtek wired NIC (which also always worked) with the same results. Network Manager says Connected to my network like it should, but no cigar. No firewall running, MoBlock is installed (and was working) but is not running. Any clues here? I apologize if this is posted elsewhere in here, but I haven't been able to find it. I'm on a XP machine that I can still reach the web with. Thanks very much in advance for any help you may provide.

Signed, 
Tired of Microsoft

---

### Post by TiredBird on 2009-09-27
[Try this link]("http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html"). I've had a lot of network issues lately and this is one of the best.

I've always had troubles with Network Manager. I finally switched to 'wicd' and have been very happy. You might want to consider that. It works well for hard links and wireless, static or dhcp and mixed in any combination with encryption or not.

---

### Post by denver on 2009-09-27
Lets see if we can figure out exactly where everithing dies. Run the following commands in a terminal:

```
host google.com #test your default nameservers
host google.com 208.67.222.222 #test using OpenDNS nameservers
ping -c3 208.67.222.222 #ping openDNS servers
ping -c3 <your gateway's IP here>
mtr 208.67.222.222 #trace the route to the openDNS nameserver
telnet google.com 80 # connect to google.com on port 80
```

These commands should give us a better idea of where the failure occurs.

---

### Post by Skyleaper on 2009-09-27
Ok, Here is the output:

```
ron@ron-laptop:~$ host google.com 
google.com has address 74.125.67.100
google.com has address 74.125.127.100
google.com has address 74.125.45.100
google.com mail is handled by 10 google.com.s9b1.psmtp.com.
google.com mail is handled by 10 google.com.s9a2.psmtp.com.
google.com mail is handled by 10 google.com.s9b2.psmtp.com.
google.com mail is handled by 100 smtp2.google.com.
google.com mail is handled by 10 google.com.s9a1.psmtp.com.
google.com mail is handled by 100 smtp1.google.com.

ron@ron-laptop:~$ host google.com 208.67.222.222
;; connection timed out; no servers could be reached

ron@ron-laptop:~$ ping -c3 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=50 time=27.9 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=50 time=30.0 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=50 time=30.4 ms

--- 208.67.222.222 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 27.957/29.463/30.431/1.079 ms

ron@ron-laptop:~$ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=3.33 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.959 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.986 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.959/1.758/3.331/1.112 ms

ron@ron-laptop:~$ mtr -r 208.67.222.222
HOST: ron-laptop                  Loss%   Snt   Last   Avg  Best  Wrst StDev
  1. 192.168.1.1                   0.0%    10    0.8   0.8   0.7   0.9   0.1
  2. 73.93.112.1                   0.0%    10    8.4   9.4   7.4  17.7   3.0
  3. 68.85.150.49                  0.0%    10    8.5   9.0   7.2  12.2   1.6
  4. te-8-3-ar01.beaverton.or.bve  0.0%    10    9.4   9.8   8.2  13.5   1.8
  5. te-0-4-0-1-cr01.portland.or.  0.0%    10   12.0  14.2  11.3  24.9   4.0
  6. pos-1-14-0-0-cr01.sacramento  0.0%    10   24.9  26.2  24.3  35.8   3.4
  7. pos-0-9-0-0-cr01.sanjose.ca.  0.0%    10   28.0  29.2  26.3  38.3   3.6
  8. te3-3.mpd01.sjc04.atlas.coge  0.0%    10   30.0  30.3  27.5  42.2   4.5
  9. 38.104.140.46                 0.0%    10   28.6  33.6  27.4  70.4  13.1
 10. resolver1.opendns.com         0.0%    10   28.1  28.7  27.2  30.2   0.9

ron@ron-laptop:~$ telnet google.com 80
Trying 74.125.127.100...
Trying 74.125.67.100...
Trying 74.125.45.100...
telnet: Unable to connect to remote host: Connection refused
```

---

### Post by jre on 2009-09-30
I´m not at all sure about these things, but:

> **Skyleaper said:**
>  No firewall running, MoBlock is installed (and was working) but is not running.

Are you really sure? The "connection refused" may well be because of moblock. Please post your iptables rules ("sudo iptables -L -nv").
Also check /var/log/moblock.log. If any IP was blocked it will be listed there.

---

### Post by Skyleaper on 2009-09-30
Thanks for the response! :) I did the IPTables listing and here it is

```
ron@ron-laptop:~$ sudo iptables -L -nv
[sudo] password for ron: 
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       68.87.69.150         0.0.0.0/0           tcp flags:!0x17/0x02 
   26  3052 ACCEPT     udp  --  *      *       68.87.69.150         0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       68.87.85.102         0.0.0.0/0           tcp flags:!0x17/0x02 
    0     0 ACCEPT     udp  --  *      *       68.87.85.102         0.0.0.0/0           
  121  8840 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
    0     0 INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 1 packets, 329 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.101        68.87.69.150        tcp dpt:53 
   26  1669 ACCEPT     udp  --  *      *       192.168.1.101        68.87.69.150        udp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       192.168.1.101        68.87.85.102        tcp dpt:53 
    0     0 ACCEPT     udp  --  *      *       192.168.1.101        68.87.85.102        udp dpt:53 
  121  8840 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    6   821 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
  121  5452 OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  *      *       192.168.1.101        0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       192.168.1.101        0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       192.168.1.1          0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:43785 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:43785 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  121  5452 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  112  5056 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
  121  5452 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            192.168.1.101       
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:43785 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:43785 
  121  5452 LSO        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

```Hope this helps. Thanks for your help!

Almost forgot, the Moblock.log file was empty? hmmm

---

### Post by Skyleaper on 2009-10-01
Something else comes to mind, I can't print anything to a stand alone network printer that is connected through an ethernet cable. It was working until this mess started.

---

### Post by jre on 2009-10-03
You were right moblock is indeed not running. Since it´s not running, the empty logfile is ok.
Further i can´t see any problems of blocked packets by any other iptables rules. But since I don´t understand them 100%, you *might* completely disable any firewall settings, although I doubt this is really necessary (NOTE: everything after "#" is just a comment:
```
sudo iptables-save > test # This saves your current iptables settings in a file "test"
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo  iptables -P OUTPUT ACCEPT
# Now all (IPv4) traffic is accepted, so test it again
sudo iptables-restore < test # Restore your old setup
```

Good luck in solving your problems, sorry I couldn´t help.

---

### Post by Skyleaper on 2009-10-03
JRE, Thanks for the help! Flushing and resetting the iptables got me working again. I'll have to re-tweek my iptables a bit because I'm accepting everything at the moment, but it is a start and connected to the net again! Thanks to all who were kind enough to reply.

Sky

---

### Post by jre on 2009-10-04
Woops, and I thought I were to pedantic ;-)
Glad I wrote that anyway.

---

