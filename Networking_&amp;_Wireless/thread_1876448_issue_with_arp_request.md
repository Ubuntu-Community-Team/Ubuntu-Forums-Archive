---
title: "issue with arp request"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by morris_horesh on 2011-11-06
Hi,

I am running the following Ubuntu version:
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux



The box receives its IP address from a router that runs a dhcp server:

```

[FONT=Courier New]eth0      Link encap:Ethernet  HWaddr XX:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT]
[FONT=Courier New]          inet addr:[/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New]  Bcast:[/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New]  Mask:255.255.255.255
          inet6 addr: YYY::[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4345 errors:1 dropped:0 overruns:0 frame:1
          TX packets:7908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:783937 (783.9 KB)  TX bytes:1294569 (1.2 MB)
          Interrupt:23
[/FONT]
[FONT=Courier New]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New]     0.0.0.0         UG    100    0        0 eth0
[/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA  [/FONT][FONT=Courier New]   0.0.0.0         255.255.255.255 UH    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
[/FONT]

```Whenever the box needs to reach a host on the internet, it first broadcasts a ARP request (who has "some internet host" address) on eth0. The reply is always the MAC address of the router.

If I'm not mistaken, when the box attempts to connect to a host outside of its network (all hosts are outside of this boxes network because of the network mask), it should search for the MAC address of its default gateway (if the address is not already in the ARP table) and send the frame to that address. It shouldn't search for MAC addresses of hosts outside its network.

What is causing that behavior ?

---

### Post by bab1 on 2011-11-06
> **morris_horesh said:**
> Hi,

I am running the following Ubuntu version:
3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux



The box receives its IP address from a router that runs a dhcp server:

```

[FONT=Courier New]eth0      Link encap:Ethernet  HWaddr XX:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]XX[/FONT]
[FONT=Courier New]          inet addr:[/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New]  Bcast:[/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New]  Mask:255.255.255.255
          inet6 addr: YYY::[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]:[/FONT][FONT=Courier New]YYY[/FONT][FONT=Courier New]/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4345 errors:1 dropped:0 overruns:0 frame:1
          TX packets:7908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:783937 (783.9 KB)  TX bytes:1294569 (1.2 MB)
          Interrupt:23
[/FONT]
[FONT=Courier New]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New]     0.0.0.0         UG    100    0        0 eth0
[/FONT][FONT=Courier New]AA.[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA[/FONT][FONT=Courier New].[/FONT][FONT=Courier New]AA  [/FONT][FONT=Courier New]   0.0.0.0         255.255.255.255 UH    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
[/FONT]

```Whenever the box needs to reach a host on the internet, it first broadcasts a ARP request (who has "some internet host" address) on eth0. The reply is always the MAC address of the router.

If I'm not mistaken, when the box attempts to connect to a host outside of its network (all hosts are outside of this boxes network because of the network mask), it should search for the MAC address of its default gateway (if the address is not already in the ARP table) and send the frame to that address. It shouldn't search for MAC addresses of hosts outside its network.

What is causing that behavior ?

I think you will find this is because your host ("the box") is the only host in the broadcast domain (255.255.255.255).  As your host is not the destination and there will be no other replies, the default gateway is where the the packet is direct to.

---

### Post by morris_horesh on 2011-11-06
Oh, I should have thought of it myself. Is there any way to get around it ? Depending on the network activity, the ARP table may grow ridiculously large to the point where I can't communicate with hosst that are not in it already. Only restarting the network service resolves the situation.

---

### Post by bab1 on 2011-11-06
> **morris_horesh said:**
> Oh, I should have thought of it myself. Is there any way to get around it ? Depending on the network activity, the ARP table may grow ridiculously large to the point where I can't communicate with hosst that are not in it already. Only restarting the network service resolves the situation.

You have seen this happen?  The only thing in the arp table should be the host.  This is mapping of *local link* MAC addresses to IP addresses available in the broadcast domain and you domain is only the single host.

Try a broadcast ping like this ```
ping -c4 -b <the_broadcast_address>
```
Then provide the output of ```
arp -a
```

---

### Post by morris_horesh on 2011-11-06
Well, I couldn't connect to hosts on the internet, I saw the message "Neighbour table overflow" in the system log and arp -na returned a rather large list.

The truth of the matter is that I don't think I saw this before I upgraded to 11.10 although I cannot be absolutely sure.


BTW I now have 383 entries in the ARP table (arp -na | grep "" -c)

---

### Post by bab1 on 2011-11-06
> **morris_horesh said:**
> Well, I couldn't connect to hosts on the internet, I saw the message "Neighbour table overflow" in the system log and arp -na returned a rather large list.

The truth of the matter is that I don't think I saw this before I upgraded to 11.10 although I cannot be absolutely sure.


BTW I now have 383 entries in the ARP table (arp -na | grep "" -c)

What this tell me is that EVERYTHING is a neighbor.  Maybe your IP addressing is conflicting with a larger network.

Here is my arp cache```
arp -na
? (192.168.1.151) at 00:15:c5:47:94:25 [ether] on eth0
? (192.168.1.1) at 00:0f:db:b5:44:d8 [ether] on eth0

```

Here is the same a shown by iproute2 command.```
ip neighbor show
192.168.1.151 dev eth0 lladdr 00:15:c5:47:94:25 STALE
192.168.1.1 dev eth0 lladdr 00:0f:db:b5:44:d8 STALE

```

One address is a laptop that my wife is using (about 1 meter away) and the other is the router.  Note that they are both listed as stale as I am not talking directly to either device.  I am visiting sights on the Internet however.

Once again, if you have properly set up the interface it should only cache its neighbors in a LAN (local links).

---

### Post by morris_horesh on 2011-11-06
I am not quite sure I understand what the conflict could be. Here is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0


```

I have dhcpd and bined9 servers that are running. They serve computers in the 192.168.2.xxx network. This linux box is their default gateway and it has iptables NAT configuration to serve that network as well.

---

### Post by bab1 on 2011-11-06
> **morris_horesh said:**
> I am not quite sure I understand what the conflict could be. Here is my /etc/network/interfaces file:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.2.1
netmask 255.255.255.0


```

I have dhcpd and bined9 servers that are running. They serve computers in the 192.168.2.xxx network. This linux box is their default gateway and it has iptables NAT configuration to serve that network as well.

I had a suspicion that this host was really a router.  Have you talked to the administrators upstream (ISP?).  The upstream network should be a reasonable size and therefore should have a more suitable subnet mask for the eth1 interface.  maybe this is a misconfiguration on their part.

I realize you don't control that interface, but it is hammering your router.  Everything you are doing on the LAN side is reasonable.  

The only other thing I could suggest is that you tune the kernel IP stack yourself.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.serveradminblog.com/2011/02/neighbour-table-overflow-sysctl-conf-tunning/") and [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://blog.lachmann.org/?p=204") for some ideas.

---

### Post by morris_horesh on 2011-11-06
The next piece of equipment after my linux box is a DLink ADSL modem that is connected via ethernet to my box on eth0. On the other side, the DLink modem is connected via ADSL to the ISP:

[192.168.2.xxx network]->[linux box eth1]->[linux box eth0]->[DLink eth]->[DLink ADSL]->[ISP]

The ADSL modem supplies eth0 with its network parameters via dhcp. Everything the box knows about the network comes from the modem. What could the modem be telling the box about the network that would make the box think that everything is a neighbor ?

---

### Post by bab1 on 2011-11-06
> **morris_horesh said:**
> The next piece of equipment after my linux box is a DLink ADSL modem that is connected via ethernet to my box on eth0. The other side, the DLink modem is connected via ADSL to the ISP:

[192.168.2.xxx network]->[linux box eth1]->[linux box eth0]->[DLink eth]->[DLink ADSL]->[ISP]

The ADSL modem supplies eth0 with its network parameters via dhcp. Everything the box knows about the network comes from the modem. What could the modem be telling the box about the network that would make the box think that everything is a neighbor ?

I'm just guessing here, but it appears that you have bridged the modem (or it came that way) to allow you to directly connect to your ISP's network.  Their network is suppling you with the IP address and should be supplying you with the correct subnet mask for that interface.  Do you understand subnet masking?  Is this a production environment or are you experimenting?

---

### Post by morris_horesh on 2011-11-06
Yes, I do understand subnet masking and no, this is not a production environment. This is my home network.

here is what tcpdump has to say:
```

01:15:42.003291 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 328)
    AA.AA.AA.AA> 192.168.1.1.bootps: [udp sum ok] BOOTP/DHCP, Request from XX:XX:XX:XX:XX:XX (oui Unknown), length 300, xid 0x1a4e0834, Flags [none] (0x0000)
          Client-IP AA.AA.AA.AA
          Client-Ethernet-Address XX:XX:XX:XX:XX:XX (oui Unknown)
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Request
            Hostname Option 12, length 4: "htpc"
            Parameter-Request Option 55, length 13:
              Subnet-Mask, BR, Time-Zone, Default-Gateway
              Domain-Name, Domain-Name-Server, Option 119, Hostname
              Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
              NTP
01:15:42.006731 IP (tos 0x0, ttl 64, id 0, offset 0, flags [none], proto UDP (17), length 576)
    192.168.1.1.bootps > AA.AA.AA.AA: [udp sum ok] BOOTP/DHCP, Reply, length 548, xid 0x1a4e0834, Flags [none] (0x0000)
          Client-IP AA.AA.AA.AA
          Your-IP AA.AA.AA.AA
          Client-Ethernet-Address XX:XX:XX:XX:XX:XX (oui Unknown)
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: ACK
            Server-ID Option 54, length 4: 192.168.1.1
            Lease-Time Option 51, length 4: 60
            Hostname Option 12, length 4: "htpc"
            Subnet-Mask Option 1, length 4: 255.255.255.255
            Default-Gateway Option 3, length 4: AA.AA.AA.AA
            Domain-Name-Server Option 6, length 4: DNS.DNS.DNS.DNS


```

BTW, thanks for your patience.

---

### Post by bab1 on 2011-11-06
> **morris_horesh said:**
> Yes, I do understand subnet masking and no, this is not a production environment. This is my home network.

here is what tcpdump has to say:
```

01:15:42.003291 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 328)
    AA.AA.AA.AA> 192.168.1.1.bootps: [udp sum ok] BOOTP/DHCP, Request from XX:XX:XX:XX:XX:XX (oui Unknown), length 300, xid 0x1a4e0834, Flags [none] (0x0000)
          Client-IP AA.AA.AA.AA
          Client-Ethernet-Address XX:XX:XX:XX:XX:XX (oui Unknown)
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: Request
            Hostname Option 12, length 4: "htpc"
            Parameter-Request Option 55, length 13:
              Subnet-Mask, BR, Time-Zone, Default-Gateway
              Domain-Name, Domain-Name-Server, Option 119, Hostname
              Netbios-Name-Server, Netbios-Scope, MTU, Classless-Static-Route
              NTP
01:15:42.006731 IP (tos 0x0, ttl 64, id 0, offset 0, flags [none], proto UDP (17), length 576)
    192.168.1.1.bootps > AA.AA.AA.AA: [udp sum ok] BOOTP/DHCP, Reply, length 548, xid 0x1a4e0834, Flags [none] (0x0000)
          Client-IP AA.AA.AA.AA
          Your-IP AA.AA.AA.AA
          Client-Ethernet-Address XX:XX:XX:XX:XX:XX (oui Unknown)
          Vendor-rfc1048 Extensions
            Magic Cookie 0x63825363
            DHCP-Message Option 53, length 1: ACK
            Server-ID Option 54, length 4: 192.168.1.1
            Lease-Time Option 51, length 4: 60
            Hostname Option 12, length 4: "htpc"
            Subnet-Mask Option 1, length 4: 255.255.255.255
            Default-Gateway Option 3, length 4: AA.AA.AA.AA
            Domain-Name-Server Option 6, length 4: DNS.DNS.DNS.DNS


```

BTW, thanks for your patience.

You have blocked out the pertinent information.  I can't directly comment when I don't have information.

Did your ISP advise you to use DHCP on the WAN side?  Is the DHCP server local to the WAN address (in the same subnet)?  Did the ISP tell you that a subnet mask of 255.255.255.255 was correct?  I would expect to see a /24 or a /23 network. (255.255.255.0 or 255.255.248.0).

---

### Post by morris_horesh on 2011-11-06
AA.AA.AA.AA is the ip address assigned to me by the ISP.
192.168.1.1 is the management ip address of the modem.
XX:XX:XX:XX:XX:XX is the MAC address of eth0 on the linux box.

the dhcp server on the modem says that we're assign the ip address AA.AA.AA.AA, our network mask is 255.255.255.255 and our DNS server is at the ip DNS.DNS.DNS.DNS

Is there other information that you need ?

My ISP may assign a different ip address every time I connect and so I must use dhcp.

---

### Post by bab1 on 2011-11-06
> **morris_horesh said:**
> AA.AA.AA.AA is the ip address assigned to me by the ISP.
192.168.1.1 is the management ip address of the modem.
XX:XX:XX:XX:XX:XX is the MAC address of eth0 on the linux box.

the dhcp server on the modem says that we're assign the ip address AA.AA.AA.AA, our network mask is 255.255.255.255 and our DNS server is at the ip DNS.DNS.DNS.DNS

Is there other information that you need ?

My ISP may assign a different ip address every time I connect and so I must use dhcp.

I wasn't really asking for more information.  I can't fix it from where I sit anyway.  I don't believe you can either.  I was trying to give you the information *you need *when you speak to your ISP.

The WAN address is owned (managed) by the ISP.  Typically this is an ATM circuit. This is usually terminated with a residential gateway (a router) with an ATM configured interface.  

As I said before; *you need to talk to your ISP*.  The things you need to go over are the mode that your modem is working in (ATM or Ethernet) and the configuration the ISP uses to provide you with an IP address and a reasonable subnet mask.

---

### Post by morris_horesh on 2011-11-06
OK. Thanks a lot.

---

### Post by morris_horesh on 2011-12-05
I ended up adding the following hourly cron job:

```

#!/bin/sh
ip link set arp off dev eth0
ip link set arp on dev eth0

``` 

It takes a few seconds before the arp table is actually cleaned. I also increased the size of the arp table to 8192.

---

### Post by diablo75 on 2011-12-05
Why is the subnet mask set to block out all 32 bits?  The function of the mask is to divide an IP address into Network bits and Host bits.  Typically, in a home network, the last octet is for hosts (computers/routers, etc) on a network, and the first three octets are the network that "houses" those hosts.  If you set the mask to block out all bits as network then there is no room left for any bits to be used for a host address, including your own computer (in theory).

---

### Post by diablo75 on 2011-12-05
> **morris_horesh said:**
> Whenever the box needs to reach a host on the internet, it first broadcasts a ARP request (who has "some internet host" address) on eth0. The reply is always the MAC address of the router.

I think you are confusing ARP with Domain Name Resolution.  ARP is a link-layer protocol used to call out to a DHCP server (your router, typically) to assign your computer an available IP address on the network.  It does this by basically saying, "Hello, my MAC address is xx.xx.xx.xx.xx.xx. Do you have an IP address for me?"  And the router says, "Yes, here's one that's free to use.  I shall write down your MAC and IP address in my routing table for future reference so if I see any requests directed towards your IP I will know which MAC address to forward the packet to."

Once it's assigned connection requests for stuff beyond your network (e.g., the Internet) involves Domain Name Resolution and have nothing to do with ARP.  Your computer sends a query to either a DNS server directly (through the router) or to the router itself (which passes it off to the DNS servers it's learned of via your ISP).  The DNS responds with the answer and says, "The IP address of google.com is 173.194.64.105, sir."  Then your computer goes, "Okay, send this packet to 173.194.64.105 and store this address in my DNS cache."  Again, ARP has nothing to do with this.

---

### Post by jonobr on 2011-12-05
> I think you are confusing ARP with Domain Name Resolution. ARP is a link-layer protocol used to call out to a DHCP server (your router, typically) to assign your computer an available IP address on the network. It does this by basically saying, "Hello, my MAC address is xx.xx.xx.xx.xx.xx. 

Above is a description of the bootp process not arp.

Arp is for obtaining mac addresses from other devices whos mac is unknown but whos IP address is.

---

### Post by bab1 on 2011-12-05
> **jonobr said:**
> Above is a description of the bootp process not arp.

Arp is for obtaining mac addresses from other devices whos mac is unknown but whos IP address is.

Hope this doesn't confuse the OP but:
*"The Dynamic Host Configuration Protocol (DHCP) is a more advanced protocol for the same purpose and has superseded the use of BOOTP. Most DHCP servers also function as BOOTP servers."*  As noted [**[COLOR="Blue"][B]here**[/COLOR][/B]]("http://en.wikipedia.org/wiki/Bootstrap_Protocol").

---

### Post by morris_horesh on 2011-12-06
> **diablo75 said:**
> I think you are confusing ARP with Domain Name Resolution.  ARP is a link-layer protocol used to call out to a DHCP server (your router, typically) to assign your computer an available IP address on the network.  It does this by basically saying, "Hello, my MAC address is xx.xx.xx.xx.xx.xx. Do you have an IP address for me?"  And the router says, "Yes, here's one that's free to use.  I shall write down your MAC and IP address in my routing table for future reference so if I see any requests directed towards your IP I will know which MAC address to forward the packet to."

Once it's assigned connection requests for stuff beyond your network (e.g., the Internet) involves Domain Name Resolution and have nothing to do with ARP.  Your computer sends a query to either a DNS server directly (through the router) or to the router itself (which passes it off to the DNS servers it's learned of via your ISP).  The DNS responds with the answer and says, "The IP address of google.com is 173.194.64.105, sir."  Then your computer goes, "Okay, send this packet to 173.194.64.105 and store this address in my DNS cache."  Again, ARP has nothing to do with this.

Well, I do know the difference between DNS and ARP and I can assure you that these are ARP requests. DNS requests do not add entries to the arp table. I do have a MAC address for google.com's ip in the arp table and it is the MAC address of the ADSL modem. In fact, every address on the internet with which I communicate is listed in the arp table with the MAC address of the ADSL modem.

here is one of the entries (#arp -n | grep 209.85.148.103):
```

209.85.148.103           ether   XX:XX:XX:XX:XX:XX   C                     eth0

```whois will tell you that 209.85.148.103 belongs to google. Now, what is google.com's ip address doing in my arp table ?

I suspect it has something to do with the network mask. The problem is that it is assigned by the ISP. I assume this is how their network works.

---

### Post by morris_horesh on 2011-12-06
> **diablo75 said:**
> Why is the subnet mask set to block out all 32 bits?  The function of the mask is to divide an IP address into Network bits and Host bits.  Typically, in a home network, the last octet is for hosts (computers/routers, etc) on a network, and the first three octets are the network that "houses" those hosts.  If you set the mask to block out all bits as network then there is no room left for any bits to be used for a host address, including your own computer (in theory).

The subnet mask is given by the ISP along with the IP address, DNS server and so forth via DHCP.

---

### Post by matt_symes on 2011-12-06
Hi

> **diablo75 said:**
> I think you are confusing ARP with Domain Name Resolution.  ARP is a link-layer protocol used to call out to a DHCP server (your router, typically) to assign your computer an available IP address on the network.  It does this by basically saying, "Hello, my MAC address is xx.xx.xx.xx.xx.xx. Do you have an IP address for me?"  And the router says, "Yes, here's one that's free to use.  I shall write down your MAC and IP address in my routing table for future reference so if I see any requests directed towards your IP I will know which MAC address to forward the packet to."

Once it's assigned connection requests for stuff beyond your network (e.g., the Internet) involves Domain Name Resolution and have nothing to do with ARP.  Your computer sends a query to either a DNS server directly (through the router) or to the router itself (which passes it off to the DNS servers it's learned of via your ISP).  The DNS responds with the answer and says, "The IP address of google.com is 173.194.64.105, sir."  Then your computer goes, "Okay, send this packet to 173.194.64.105 and store this address in my DNS cache."  Again, ARP has nothing to do with this.

This is wrong. Sorry. It seems to me you are mixing to protocols.

This may clarify things.

Arp.

[http://www.art0.org/networking/the-arp-protocol-explained](http://www.art0.org/networking/the-arp-protocol-explained)

Bootp.

[http://en.wikipedia.org/wiki/Bootstrap_Protocol](http://en.wikipedia.org/wiki/Bootstrap_Protocol)

Kind regards

---

### Post by diablo75 on 2011-12-06
Clearly I need to brush up on my networking.  It has been since 2007 since I took a CCNA class.  Wow... time flies.  Sorry for the bad info I gave earlier.

---

