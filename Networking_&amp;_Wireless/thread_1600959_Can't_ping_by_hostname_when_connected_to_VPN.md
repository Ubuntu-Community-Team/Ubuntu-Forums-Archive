---
title: "Can't ping by hostname when connected to VPN"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by tram4 on 2010-10-19
I am running Ubuntu 10.04.  I installed winbind and added the wins in /etc/nsswitch.conf.

It now works when I ping Windows machines by hostname and returns with the IP.  As soon as I connect to a VPN network (Windows network), I am unable to ping by hostname.  I am able to ping by IP only.  When I ping with hostname, It returns with "unknown host".  I'm using vpnc.  Any ideas?

Thanks.

---

### Post by Sergius14 on 2010-10-19
WINS servers are in the same network as you are?

One possibility is that WINS are in a different Network and when you connect to the VPN, your Default Gateway changes to the VPN and WINS are no more accesible.

To check try this and paste the results.


Your IP and network mask.

```
ifconfig -a
```WINS servers IP.

routes before VPN is connected.
routes after VPN is connected.

```
route -v
```
Regards,

---

### Post by tram4 on 2010-10-20
Hi.  Thanks for the reply.  Not sure what you mean by WINS servers.  When I said "wins" it's the code that I added to the /etc/nsswitch.conf file to get ping by pc name working (see red text):

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          **[COLOR=Red]files wins[/COLOR]** mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```*This along with installing winbind is what made ping by PC name working.


[B]Here's what I got when just connected regularly to my local network with your instructions (PING BY PC NAME IS WORKING):

ifconfig -a:

[/B]```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:e6:ac:d5  
          inet addr:192.168.142.131  Bcast:192.168.142.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee6:acd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73380712 (73.3 MB)  TX bytes:7294090 (7.2 MB)
          Interrupt:18 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22128 (22.1 KB)  TX bytes:22128 (22.1 KB)
```[B]route -v:
[/B]
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.142.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.142.1   0.0.0.0         UG    0      0        0 eth0

```**When connected to external network via VPN (PING BY PC NAME [COLOR=Red]NOT[/COLOR] WORKING):**

**ifconfig -a:**

```
eth0      Link encap:Ethernet  HWaddr 00:0c:29:e6:ac:d5  
          inet addr:192.168.142.131  Bcast:192.168.142.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee6:acd5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73427773 (73.4 MB)  TX bytes:7311177 (7.3 MB)
          Interrupt:18 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22128 (22.1 KB)  TX bytes:22128 (22.1 KB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.1.187  P-t-P:192.168.1.187  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:960 (960.0 B)  TX bytes:492 (492.0 B)
```**route -v:**

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
mail.company 192.168.142.1   255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 tun0
192.168.15.0    *               255.255.255.0   U     0      0        0 tun0
192.168.250.0   *               255.255.255.0   U     0      0        0 tun0
192.168.251.0   *               255.255.255.0   U     0      0        0 tun0
192.168.12.0    *               255.255.255.0   U     0      0        0 tun0
192.168.11.0    *               255.255.255.0   U     0      0        0 tun0
192.168.10.0    *               255.255.255.0   U     0      0        0 tun0
192.168.142.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.142.1   0.0.0.0         UG    0      0        0 eth0
```[B]Thanks again.
[/B]

---

### Post by Sergius14 on 2010-10-20
Over Windows it is not the same to ping a hostname to ping a FQDN

Ex.

ping computer-01

ping computer-01.domain.local

The first one, tries to resolve the name over NetBIOS (over TCP/IP). If you don't have NetBIOS or you are outside your network (NetBIOS naming works only at broadcast level) you have to use WINS server.

Generally, a Windows DNS servers is also enabled to serve WINS.


Your VPN may change your DNS when you connect.


Check (and double check) your DNS before and after VPN.

Maybe you are having Internet because both are redirecting to Inet, but it doesn't work for local domain names.

That's very frequent with VPN access, with also a default route change (that's called tunnel mode VPN).

Let us known what you find out.


On termina you may use this commands:

nslookup

-> server x.x.x.x (to connect to other DNS servers other than defaults)

Regards,

---

### Post by SeijiSensei on 2010-10-20
> **tram4 said:**
> I am running Ubuntu 10.04.  I installed winbind and added the wins in /etc/nsswitch.conf.

It now works when I ping Windows machines by hostname and returns with the IP.  As soon as I connect to a VPN network (Windows network), I am unable to ping by hostname.  I am able to ping by IP only.  When I ping with hostname, It returns with "unknown host".  I'm using vpnc.  Any ideas?

Thanks.

What DNS servers are you using when connected via vpnc?  Are they the same as your DNS servers wnen you're not running the VPN?  Does the contents of /etc/resolv.conf change when you connect to the VPN?

---

### Post by tram4 on 2010-10-21
It does seem to be changing the resolv.conf file when I connect to VPN

**NO VPN Connection:**

```
# Generated by NetworkManager
domain internal.local
search internal.local
nameserver 192.168.130.5
nameserver 209.226.51.10
```**With VPN Connection:**

```
# Generated by NetworkManager
domain internal.local
search internal.local
nameserver 192.168.1.31
nameserver 192.168.12.33
nameserver 192.168.130.5
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 209.226.51.10
```

---

### Post by Sergius14 on 2010-10-21
Mmmm it is very possible.

Many ppl think that adding 2 o more DNS to resolve different domains would work, but it fact it doesn't.

DNS querys **always** works by asking the first domain. If that domain says that that query can't be resolve, the answer is that: domain unknown. Can't resolve a domain is a correct reply so there is no need to ask to the secondary.

The secondary domain are only used by when the primary gives times out a couple of times (and I think that also when doesn't response to ping). However, I'm tired of seeing that when the primary is out it never asking to the secondary. So the primary DNS has to be the one to resolve all domains an has to be a good server.

So, the addition of the new DNS to the top of the list has to be causing you this issue.


After you connect the VPN, edit resolv.conf to delete the new DNS and left only your internal DNS (I think that is 192.168.130.5).

Never add two o more DNS to resolve different domains.

Like adding an primary internal DNS for the local domain and public DNS as secondary for internet browsing. That is not going to work or is doomed to fail.

Connect to the VPN, the edit resolv.conf with only this:

```
# Generated by NetworkManager
domain internal.local
search internal.local
nameserver 192.168.130.5
```



Update us after this new change.


Regards,

---

### Post by tram4 on 2010-10-22
This worked, but I had to change

```

domain internal.local
search internal.local
```

to

```

domain company.local
search company.local
```

This gets overwritten each time by NetworkManager, so as a workaround, I edited the VPN connection settings. under IPV4 Settings: Method: Automatic VPN Addresses Only and manually entered the DNS servers and put "company.local" under "Search Domains". 

This is ok, since the DNS addresses will never change.  I suppose there is some sort of bug in Network manager, because it's not receiving or applying the proper DNS info to the resolv.conf file.

Thanks again.

---

### Post by Sergius14 on 2010-10-22
You are welcome.  I'm glad to hear that you could find a solution.  Remember to change the subject of this threat to Solved by using the forum tools   Regards,

---

### Post by SeijiSensei on 2010-10-23
> **tram4 said:**
> This worked, but I had to change

```

domain internal.local
search internal.local
```

to

```

domain company.local
search company.local
```

This gets overwritten each time by NetworkManager, so as a workaround, I edited the VPN connection settings. under IPV4 Settings: Method: Automatic VPN Addresses Only and manually entered the DNS servers and put "company.local" under "Search Domains".

If you use "search company.local internal.local", the resolver will try both extensions when handling unqualified hostnames.  It will try host.company.local first, then host.internal.local.  The "domain" directive should include only your primary domain.

Also you can control how your DNS resolver gets modified by editing /etc/dhcp3/dhclient.conf.  You'll see that the DHCP client requests things like the DNS servers.  You can disable these requests entirely, or use the "prepend" directive to add items to the top of /etc/resolv.conf.  My guess is that NetworkManager makes some of these modifications for you.

---

