---
title: "Internet Connection Sharing Issue"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by WhiteyWan on 2010-02-03
I am using the guide shown here

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
(just the basic setup without anything below the Advanced Setup section) to try & set up Internet connection sharing to my PS3.

I'm using 9.04 Jaunty.

My setup is as follows:

Wireless card wlan0 (currently assigned 192.168.1.106 by DHCP) grabs internet from my router at 192.168.1.254. Attempting to bridge internet to eth0 (just using what is provided in the instructions, 192.168.0.1)

For the gateway setup section I only modified two lines:
```
sudo ifconfig eth1 192.168.0.1
```to show eth0

and 

```
sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT

```to 

```
sudo iptables -A FORWARD -i wlan0 -o eth0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT 
```I didn't use the instructions for setting up client as it is PS3 not a Ubuntu box but it shows as follows:

IP: 192.168.0.100 (also tried .101)
Subnet mask: 255.255.255.0
Default Router: 192.168.0.1
For DNS tried using my router (192.168.1.254), my DNS IP's that were in the router and also the openDNS ones that were listed in the instructions.

PS3 holds on "Connecting to Internet" & gives me "An error occurred during communication with the server. This is a DNS error. (80710102)" message.

Also, something I've noticed is that when I assign eth0 its IP it initially goes through and shows "192.168.1.254" when I type in ifconfig but somewhere along the line that part gets dropped...right now my ifconfig shows:

```
eth0      Link encap:Ethernet  HWaddr 00:01:6c:b7:e7:fe  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:feb7:e7fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47382 (47.3 KB)  TX bytes:10163 (10.1 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63200 (63.2 KB)  TX bytes:63200 (63.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:c5:c3:1a  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fec5:c31a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6599861 (6.5 MB)  TX bytes:1297301 (1.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-DF-C5-C3-1A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```I am pretty much a n00b at networking (well...and also to linux). Can anyone tell me what I'm doing wrong? Greatly appreciated :)

---

### Post by Iowan on 2010-02-03
[Here]("http://ubuntuforums.org/showthread.php?t=1397619") is a thread that may be helpful - especially the link to an even more helpful thread.

---

### Post by WhiteyWan on 2010-02-04
Thanks for the reply! I actually really liked the post that was linked to in the post mentioned in your reply (that was hard to figure out how to say!): [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874) . I found it to be very clear-cut and it also explained a lot of why you are doing what you are doing as opposed to just "do this" "do that". However, I'm still having an issue. My "sudo sysctl net.ipv4.ip_forward" is returning 1 as needed and I have set up my interfaces file as such:
```
 
auto eth0
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        broadcast 192.168.0.0
        network 192.168.0.0

```
 
as I am using eth0 to connect to my PS3 and wlan0 to connect to my wireless router (which doesn't require any reconfiguration, I believe). I think my wlan0 is at IP 192.168.1.106 but I'm not at home at the moment to double-check that.
 
I first configured the client PS3 with static IP and then with DHCP after installing the server on my computer. Its setup looks like: 
```
 
ddns-update-style none;
option domain-name "ytnet";
option domain-name-servers 192.168.1.254;     ##[COLOR=seagreen]**listed in resolv.conf**[/COLOR]
option routers 192.168.0.1;
 
default-lease-time 42300;
max-lease-time 84600;
authoritative;
 
log-facility local7;
 
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.150;
}

```
 
During connection my PS3 is obtaining IP successfully both with static & DHCP and furthermore when I turned off my DHCP server it said obtaining IP failed (did this just to triple-check that I set that up right). Still getting the DNS error. I also tried patching my ISP's DNS servers (that I founded listed in my wireless router's configuration page) and 8.8.8.8 for Google DNS. I'm still getting a DNS error when it tries to connect to the internet on my PS3...I'm stumped. Any help?

---

### Post by Iowan on 2010-02-04
> **WhiteyWan said:**
> 
```
 
auto eth0
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        broadcast [COLOR="Red"]192.168.0.0[/COLOR]
        network 192.168.0.0

```Broadcast is usually the high address (.255) With address and netmask specified, you may not need the last two lines at all.
Have you configured a gateway address? The DNS server address is outside the subnet - so machine will need to know how to get there. can you ping DNS server address from PS3?

---

### Post by WhiteyWan on 2010-02-04
So you're saying I should remove the last two lines from the interfaces file and then set up a gateway? How do I set up the gateway, cuz I assumed putting 
```
option routers 192.168.0.1;
```
in my DHCP server file was configuring the gateway...like I said in my first post, I'm a complete n00b when it comes to networking... or do I need to put a line pointing the eth0  to my wlan0 as the gateway in my interfaces file?

---

### Post by Iowan on 2010-02-04
You can try removing (or commenting out) the **network** and **broadcast** lines to see if it makes any difference - probably won't.
I checked my machines - this client gets its default gateway address from DHCP. So my setup closely resembles yours.  My server has it's WAN connection set via */etc/network/interfaces* and includes the **network** and **broadcast** lines as well as a gateway statement pointing to my modem. My server, however, is not providing ICS - the clients don't go through the server to get to modem, so that's where our systems differ.

---

### Post by WhiteyWan on 2010-02-05
Hey, thanks for the help! Found the problem...in my rc.local file line: 
```
/sbin/iptables --table nat -A POSTROUTING -o wlan0 -j MASQUERADE
```
I didn't realise the -o was supposed to indicate the internet-facing device.  I had it put as my eth0!  Everything works now, got my PS3 online!

---

