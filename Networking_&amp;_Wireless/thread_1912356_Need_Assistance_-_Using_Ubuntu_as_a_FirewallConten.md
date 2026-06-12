---
title: "Need Assistance - Using Ubuntu as a Firewall/Content Filter"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by ACMarina on 2012-01-20
We had a MAJOR meltdown at work and I've had to come up with a patch here, and I need some help.

Cable internet coming into modem, then into "Firewall" PC - second NIC goes to network switch, which is picked up by a Microsoft Windows SBS2k8 Box that handles DHCP duties.

I've got internet access at "Firewall", but don't have the foggiest how to set it up so that the rest of the network gets internet access.  The old computer caught fire (literally) and I can't get the old hard drive to plug in because the plastic melted.  

What next, gurus??

---

### Post by jonobr on 2012-01-20
Hi there


I feel for you, and want to help but Im not understanding the problem.

You have a firewall which is working correct?
It can access the internet - correct?
The Win2k DHCP is working ok , correct?
Clients accessing the internet cannot connect? Correct?
The rules on the firewall are all configured the way they were and are working , correct?

Are the clients getting a DHCP address from the win 2k machine?
Can your firewall ping the win 2k and the clients?
Can your clients ping the win2k,

Can your clients resolve dns ?


Again, could you explain the actual issue that is experience, the symptoms your seeing from the end having the trouble, and 
and any related info you may have such as contents of iptables, ifconfig results /etc/network/interfaces results.

If your saying my machine blew up I put a new one and dont know what to do now, thats a lot more complicated as we would need to know what that was running and doing. Hopefully theres a backup of that machine that gets you away from that problem but again, please provide as much information as you can.


Thanks

jonobr

---

### Post by ACMarina on 2012-01-20
""You have a firewall which is working correct?""

Well, sorta kinda.  The guy who set things up (who is no longer around) came from the cable modem (192.168.0.1) to an older LTS Ubuntu install (Static IP of 192.168.0.2).  There was a second NIC (static IP of 10.0.0.1) in the old computer.  I've replicated this as closely as I can with the hardware I have.  I'm calling this computer the "firewall".

""It can access the internet - correct?""
The "firewall" computer can, yes.  I'm replying on that computer in a server room right now.

""The Win2k DHCP is working ok , correct?""
Everything network-wise seems to be fine.  Clients can connect to SBS2k8, access to their NAS device, print, etc.  

""Clients accessing the internet cannot connect? Correct?""
Correct - the only computer that can access the internet at this point is "firewall".


""The rules on the firewall are all configured the way they were and are working , correct?""
Probably not.  The previous "firewall" was pretty badly damaged.  I am trying to work from copies that made it through the fire.

""Are the clients getting a DHCP address from the win 2k machine?""
Yeah, they sure are.  Preauthorized clients are getting reserved IP addresses (10.0.0.x) and open clients are getting DHCP assigned IP addresses (10.0.100.x)

""Can your firewall ping the win 2k and the clients?""
Nope - nothing going out.

""Can your clients ping the win2k,""
Yup, but not the "firewall"

""Can your clients resolve dns ?""
I don't think so

The end goal is to get everything running the way it was before, but I'm sure this will take baby steps.  The operator who installed the previous setup had Dansguarding running because there are publically accessible terminals that children use, so keeping things "clean" can be a priority - it's going to be a few weeks before any non-staff folks will be around, so I have time to work on that part.  Right now I'm just trying to restore internet access.

---

### Post by ACMarina on 2012-01-20
ifconfig results

```

eth0      Link encap:Ethernet  HWaddr 00:15:f2:06:xx:xx  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe06:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:154142084 (154.1 MB)  TX bytes:15381010 (15.3 MB)
          Interrupt:3 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:15:f2:06:xx:xx  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::215:f2ff:fe06:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:3 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42448 (42.4 KB)  TX bytes:42448 (42.4 KB)

```

---

### Post by ACMarina on 2012-01-20
/etc/network/interfaces as follows..

```

auto lo
iface lo inet loopback

```

---

### Post by jonobr on 2012-01-20
Can your clients ping the 10.0.0.1 interface?
if they can

In a terminal window can you 

```
cat /proc/sys/net/ipv4/ip_forward
```

if its 0 then you can enable it on the fly to see if it works

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

It may be just your ip forwarding is not enabled between interfaces

---

### Post by ACMarina on 2012-01-20
They can, but there is no response - Request Timed Out.

---

### Post by ACMarina on 2012-01-20
The result of the cat /proc/sys was "1"

---

### Post by jonobr on 2012-01-20
> The result of the cat /proc/sys was "1"

Thats good, it means ip forwarding is on

With the pinging not working, thats not making sense

can you ping 10.0.0.1 on your firewall?

Can you do an ipconfig on your clients and compare the results with the nic settings?

> 
10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0

On your server in a terminal, type


> sudo tcpdump -w trace.pcap -i any -s 1600 
do the ping from the client,
it will create a file called trace.pcap
you can post that here I will take a look at it for you.

---

### Post by ACMarina on 2012-01-20
Pinging 10.0.0.1 on this "firewall" computer does work, yeah..

The client computers have the default gateway set as 10.0.0.1, subnet mask 255.0.0.0

I ran the trace and it did create the file, but it won't open in my editor..

Edit to add..

```
ÔÃ²¡
```

---

### Post by jonobr on 2012-01-20
No problem, the trace was for the pinging issue so no problem.

Given you can ping
10.0.0.1

Can you now try the other interface for the same machine

can you try pinging 74.125.224.84
does that work? can you put that in a browser, can that work?

If neither works can you try disabling your firewall temporarily in case you put in a harsh rule that blocks more then it should?

---

### Post by ACMarina on 2012-01-20
Ping is successful from the "firewall".  Ping is not successful from the DHCP server or client connecting to the DHCP server.

Which firewall do you want me to disable? The one on the DHCP server (Windows Firewall) or the one on the "firewall" computer? I disabled the "firewall" firewall and tried all steps with the same result..

---

### Post by jonobr on 2012-01-20
So Im guessing again connection to DHCP is ok as your getting an IP address and that ping is not wokring to the itnerfaces I mention.

Still makes me think that the firwall could be blocking you from getting connected.

So if your using ufw try

```
sudo ufw stop
```
and then try ping again.

If your just using iptables
```
# /etc/init.d/iptables save
# /etc/init.d/iptables stop
```

---

### Post by ACMarina on 2012-01-20
I issued "sudo ufw disable" and it did, but still no joy in pinging.. nothing from the DHCP server or a client. Not external IPs, not 10.0.0.1, nothing.

I've got to be missing something..

---

### Post by jonobr on 2012-01-20
Can you run another trace on the firewall machine

```
sudo tcpdump -w trace.pcap -s 1600 -i any 
```

do the ping and post the results.

Try to do as quick as you can to capture as little as possible
(write the command on the cli and on ping on the client
hit enter on the cli - hit enter on the client and then after a few seconds, control c)

Post the results.

You can view the file with wireshark if you download it or install via synaptic

---

### Post by ACMarina on 2012-01-20
Edit - too long to see well..

---

### Post by jonobr on 2012-01-20
Hey there , v difficult to look at it in txt.

I was hoping you could post the pcap file here using the paper clip above (between the smiley face and the left and right arrows.)

That way I can search a lot quicket.

Until then , Ill look at your text file


Cheers

Jonobr

---

### Post by ACMarina on 2012-01-20
Emailing attachment to you..

---

### Post by jonobr on 2012-01-20
Sure thing

Waiting for it

Update- just got it.

Cheers


jonobr

---

### Post by ACMarina on 2012-01-20
Thank you sir! Take a look and let me know what you find..

---

### Post by jonobr on 2012-01-20
Interesting trace you sent,

All I am seeing is inbound traffic on the 192.169.0.1 interface, nothing on the first one.

Hate to do this to you ,

could you retry your ping test from the client to maybe google and rerun a trace this time instead of using the command with i any that you change any to the internal interface
eth1 maybe (the one with the 10.x.

---

### Post by ACMarina on 2012-01-20
> **jonobr said:**
> 
could you retry your ping test from the client to maybe google and rerun a trace this time instead of using the command with i any that you change any to the internal interface
eth1 maybe (the one with the 10.x.

How do I do that? I'm not familiar with the tracing..

---

### Post by jonobr on 2012-01-20
on the server type

```
sudo tcpdump -w trace.pcap -i eth1 -s 1600
```

from one client, if you could ping google.com

capture the trace and send

Also rereading the post, I misread something.

I asked you to ping 10.0.0.1, you said it worked ok, but I think you did that from the firewall,

I was wondering about from the client if that ping to 10.0.0.1 worked.

Given you disabled firewalls and things seemed ok, the only thing I can think of is physical issues with either the eth1 nic, the cable, the port it goes into or something else phsical.
Hopefully the traces will get to that

also could you send your routing table
> route -n

---

### Post by ACMarina on 2012-01-20
Nothing there - it says that there was 

```

0 packets captured
0 packets received by filter
0 packets dropped by kernel

```

---

### Post by jonobr on 2012-01-20
WOW

That matches the earlier trace.

From your earlier ifconfig it showed me the that eth1 was up.

Again, it almost tells me that nothing is going on on that port.
You would expect to see some kind of traffic even when idle.

Are you sure about your connectivity on eth1

maybe try 

```
dmesg | grep eth1
```
see if that shows anything, but something is really weird here.
Was this nic in the machine that blew up?

Looking again at your ifconfig 

it shows no packets on that interface at all

>           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

Somethings really odd here hopefully dmesg will show somwething.

---

### Post by ACMarina on 2012-01-20
grep eth1

```

[27649.328115] Inbound IN=eth1 OUT= MAC= SRC=10.0.0.1 DST=10.255.255.255 LEN=264 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=244 
[27649.328144] Inbound IN=eth1 OUT= MAC= SRC=10.0.0.1 DST=10.255.255.255 LEN=241 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=221 
[28118.886052] device eth1 entered promiscuous mode
[28151.497020] device eth1 left promiscuous mode
[28369.908114] Inbound IN=eth1 OUT= MAC= SRC=10.0.0.1 DST=10.255.255.255 LEN=264 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=244 
[28369.908145] Inbound IN=eth1 OUT= MAC= SRC=10.0.0.1 DST=10.255.255.255 LEN=241 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=221 

```

Nope, this machine is fresh.. nothing used from the other setup.

---

### Post by jonobr on 2012-01-20
This trace is a relief

Kinda shows inbound packets from eth1, Im back to thinking you have a misconfiguration on iptables and its rejecting everything.
Can you post iptables -L and route -n ?

Thanks

---

### Post by ACMarina on 2012-01-20
Route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

---

### Post by ACMarina on 2012-01-20
iptables -L

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  nrcns.area4.il.chicago.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  chic-cns.area4.il.chicago.comcast.net  anywhere            
ACCEPT     tcp  --  nrcns.westlandrdc.mi.michigan.comcast.net  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  nrcns.westlandrdc.mi.michigan.comcast.net  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             10.0.0.1            
INBOUND    all  --  anywhere             192.168.0.2         
INBOUND    all  --  anywhere             10.255.255.255      
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             10.0.0.0/8          state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             10.0.0.0/8          state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.2          chic-cns.area4.il.chicago.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.0.2          chic-cns.area4.il.chicago.comcast.net udp dpt:domain 
ACCEPT     tcp  --  192.168.0.2          nrcns.westlandrdc.mi.michigan.comcast.net tcp dpt:domain 
ACCEPT     udp  --  192.168.0.2          nrcns.westlandrdc.mi.michigan.comcast.net udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  base-address.mcast.net/8  anywhere            
DROP       all  --  anywhere             base-address.mcast.net/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:31416 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:31416 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251         udp dpt:mdns 
ACCEPT     udp  --  anywhere             239.255.255.250     udp dpt:1900 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state NEW 
ACCEPT     udp  --  anywhere             anywhere            state NEW 

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:http-alt 

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination 


```

---

### Post by jonobr on 2012-01-20
The routing table looks good,


Im no Iptables expert and need to look through.

I would recommend dropping all rules and restesting,

Ill go through it, but again, its not my strongest suit:-(

Update- notice you have logging enabled
could you
> cat /var/log/messages | grep UFW

---

### Post by jonobr on 2012-01-20
Hello

Im not seeing a lot wrong so far with your rules- the look pretty good...(again , no expert)

Can you check ufw logs ? or if you have firestarter on that machine it will give you more inforamtion and be easier to see whats going on?

Just checking

---

### Post by ACMarina on 2012-01-20
Gimme a few minutes - I had to run home and grab something.  I'll have it run in about 15 minutes.

---

### Post by ACMarina on 2012-01-20
Doesn't look like there's anything IN the logs.. ugh..

---

### Post by jonobr on 2012-01-23
Hey


Had any luck/joy?

Im thinking it may be a good idea to start a thread in security or server sections asking people to review your iptables config.

I may be missing something on it....

cheers....

jonobr

---

