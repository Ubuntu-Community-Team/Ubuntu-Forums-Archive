---
title: "Am I sending tons of ARP requests?  If so, why? and is this normal?"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by HousieMousie2 on 2009-05-10
I just loaded IPTraf and have been watching my own connection (eth0,) the traffic is flying by (roughly 50 per second) and most of it looks like this:

**ARP request for <various IPs> (188 bytes) from <this value remains constant> to ffffffffffff on eth0**

Is my machine generating these requests?  lol  Is this a good thing?

---

### Post by Copernicus1234 on 2009-05-10
Generating tons of arp packets can be part of cracking a wireless network using WEP encryption. Once they have generated enough packets, they can crack the key and use your network.

Running wireless with WEP?

---

### Post by HousieMousie2 on 2009-05-10
No wireless that I know of. lol  I am fairly confident that my ISP would happily be charging me more if I did have wireless.

So... my machine is not making these?

---

### Post by HousieMousie2 on 2009-05-11
Is this originating from my machine or not?

**ARP request for <various IPs> (188 bytes) from <this value remains constant> to ffffffffffff on eth0**

---

### Post by chili555 on 2009-05-11
> ARP request for <various IPs> (188 bytes) from [COLOR="Red"]<this value remains constant>[/COLOR] to ffffffffffff on eth0Is this your IP address? Check with:```
ifconfig eth0
```

---

### Post by HousieMousie2 on 2009-05-11
IPTraf is showing a "MAC address" in that location.

I do not recognize the number and it is not shown in the data from ifconfig eth0.

It is a single set of numbers and (two) letters, but not broken up with punctuation, (nor even spaces,) the way I have seen them shown before.

---

### Post by netztier on 2009-05-11
> **HousieMousie2 said:**
> 
**ARP request for <various IPs> (188 bytes) from <this value remains constant> to ffffffffffff on eth0**


if <this value remains constant> is not found anywhere as "HWaddr" in the output of **ifconfig eth0**, then it's not your machine:

```
user@host:~$ ifconfig eth0
eth0      Link encap:Ethernet  [COLOR="Red"]HWaddr 00:22:1a:b7:24:e8[/COLOR]  
          inet addr:172.20.125.31  Bcast:172.20.125.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:90697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89582682 (89.5 MB)  TX bytes:14285314 (14.2 MB)
          Interrupt:5 
```


Do you have an internet access via cable, and did you hook up your cable modem directly to eth0 of your computer?

Some cable providers group their home user customers in rather large subnet chunks, up to (theoretically) several 1000 customers per IP subnet (I see /20 subnet masks on a regular basis, makes for up to 4k IP addresses in a single subnet).

Now we know that there is an immense number of bot/worm/virus-infected PCs on the Internet. One of their tasks is to scan the network for other candidates for infection. From their bot master, they get a list of IP ranges to scan, and guess what, it's the well known IP-ranges of home broadband subnets that are subject to such scanning by bots - that's where they'll find poorly configured firewalls and unpatched operating systems without security updates.

So if they scan for a certain IP from their list (sending a TCP SYN to a possibly open TCP port), the "last" router that has a leg in the (possible) victim's IP subnet must do an ARP broadcast to find out the MAC address that belongs to that IP address. But the previous owner of that IP address might be offline - and the router will repeat it's broadcast a few times.

Now imagine this happening for several hundred IPs (some being "live", some being offline) at the same time. Then remember that ARPs are sent as Ethernet broadcasts (as can be seen by the destination address: FF:FF:FF:FF:FF:FF), and that these must be sent to *everyone* on the broadcast domain - that's where you get a good amount of the ARP traffic from.

To see if you get those ARP broadcasts from your ISPs router, look at **netstat -nr** to see the IP address of your default gateway (the one with the 0.0.0.0 Destination and 0.0.0.0 Genmask). IP addresses are from my subnet - yours will be totally different:

```
user@host:~$** netstat -nr**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.20.125.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
[COLOR="DarkRed"]0.0.0.0         [COLOR="Red"]172.20.125.1[/COLOR]    0.0.0.0         UG        0 0          0 eth0[/COLOR]

```

and then look at **arp -na** to see which MAC address your Default Gateway has:

```
user@host:~$** arp -na**
? (172.20.125.30) at 00:1a:24:33:ab:46 [ether] on eth0
? ([COLOR="Red"]172.20.125.1[/COLOR]) at [COLOR="blue"]00:14:e8:c6:29:32[/COLOR] [ether] on eth0

```

Now look back at <this value remains constant>. Is it the same? Then these ARP broadcasts are coming from your ISP's router - and it's neither the router nor the ISP's fault: If the "last router" must forward a packet to one of the ISP's customers, it *must* ARP for it - no way around that.

.oO( ceterum censeo: large subnets *do* have drawbacks! )

regards

Marc

---

### Post by HousieMousie2 on 2009-05-11
Yes, it is the same.  Thank you!  Had me worried. lol

The MAC address that showed up with ifconfig eth0, was clearly mine, or at least KNetworkManager said so.  It was just the other one that caused mild alarm.

Thank you for educating me!!!  Very much appreciated!

---

### Post by HousieMousie2 on 2009-05-11
Okay, who moved it?!?  lol  Damn, I don't see the option to Thank nor to mark the thread solved.

---

