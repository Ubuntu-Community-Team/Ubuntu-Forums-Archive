---
title: "Connecting to the Internet Using DSL"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by maembe on 2012-11-11
I just moved and ended up switching to DSL.  There are certain things that don't load properly for me in Ubuntu for some reason.  For example, I can never log in to Gmail.  Everything works just fine in Windows.

I was poking around in the network settings and noticed under "edit connections" there's a tab for DSL.  Do I need to set up this connection there?  When I try it doesn't seem like there's anywhere to actually find my internet connection.  Currently I'm just using the same connection I had when I had cable because it's the same router (under "wireless").

Anyone had any issues with DSL or know what could be wrong?

---

### Post by papibe on 2012-11-11
Hi maembe.

The DSL tab is when you don't have a router, just a modem, and you have to set your DSL account information from the computer.

I would start by cleaning cookies and temp files. If that doesn't work try reseting your Firefox profile.

Let us know how it goes.
Regards.

---

### Post by ahallubuntu on 2012-11-11
The DSL section of "Connections" is for the rare case (these days) when people use their computer to login directly to their DSL.  That means, the computer itself has a PPPoE username and password.  That's how it was commonly done in the old days.  There are probably a few people who still do it this way.

As a new user, you almost certainly have a separate modem/router that does all of this login for you automatically.  Then none of this info needs to be stored in your computer itself.  All you need is to plug in a cable to your DSL modem/router or connect wirelessly.  That is all separate from the "DSL username/password" (PPPoE or something like that) you'd use to login - all of that is set inside your DSL modem almost certainly.

How are you connecting to your DSL now?  Wired?  Wirelessly?

One thing you could do is set your DNS to use Google's DNS instead of whatever your DSL provider offers.  I'm not sure why that would fix any issue with Ubuntu vs. Windows, though.  Connecting to a router should be routine and automatic with either operating system.

---

### Post by maembe on 2012-11-11
> **ahallubuntu said:**
> 

How are you connecting to your DSL now?  Wired?  Wirelessly?

One thing you could do is set your DNS to use Google's DNS instead of whatever your DSL provider offers.  I'm not sure why that would fix any issue with Ubuntu vs. Windows, though.  Connecting to a router should be routine and automatic with either operating system.


I'm currently connecting wirelessly.  I tried changing the DNS.  I went into the connection and changed both ipv4 and ipv6 methods to "Automatic (DHCP) addresses only" and entered both of Google's DNS in "DNS Servers" leaving "Search Domains" and "DHCP client ID" blank.  I still seem to be having issues in all browsers though.

---

### Post by ahallubuntu on 2012-11-11
You may simply be having wireless connection issues that have nothing to do with DSL.  Before you moved, were you connected wirelessly to the same piece of equipment?  I'm guessing you got a new all-in-one modem/router and are wirelessly connected to that?

You could confirm that you are having wireless problems by, if possible, wiring in to your router temporarily instead of using wireless.  (If you do that, disconnect from wireless entirely.)  If that fixes your problem, then it's just a wireless problem (and a different track for troubleshooting).  But if you have the same exact issues when wired, it's nothing to do with wireless.

---

### Post by maembe on 2012-11-11
> **ahallubuntu said:**
> You may simply be having wireless connection issues that have nothing to do with DSL.  Before you moved, were you connected wirelessly to the same piece of equipment?  I'm guessing you got a new all-in-one modem/router and are wirelessly connected to that?

You could confirm that you are having wireless problems by, if possible, wiring in to your router temporarily instead of using wireless.  (If you do that, disconnect from wireless entirely.)  If that fixes your problem, then it's just a wireless problem (and a different track for troubleshooting).  But if you have the same exact issues when wired, it's nothing to do with wireless.

I am connected to the exact same router that I had when I had cable (but with a different modem obviously).  I'm trying to connect wired, but it doesn't seem to be connecting for some reason.

---

### Post by ahallubuntu on 2012-11-11
OK.  One thing to check: is the subnet used by the router different from the subnet used by the DSL modem?

What I mean is: if the router's LAN IP is 192.168.1.1 (and you get 192.168.1.X when connecting to it), is the DSL modem's IP the same 192.168.1.1?  Or is it different?  It should be different. (Change one of them to 192.168.2.1 or something like that.)  It could be this was not an issue when you had cable.

Or is your wireless router setup as an "access point" not as a router?

Try this: unplug your router temporarily from your DSL modem, and wire your computer directly to the modem.  In Ubuntu type "ifconfig" in a terminal and see what IP you get.  (Or ipconfig in Windows in a DOS window.)  (For privacy reasons, if you don't get 192.168.something or don't get 10.something, blot out the last digit of your IP.)

Now (with router still unplugged from modem) wire directly into your router into one of the LAN ports.  Repeat above.  What IP do you get?

In any case: did you re-configure the router after moving from cable to DSL?  Or did you use it as-is?  The subnet thing could be one explanation for the issues you are having.

---

### Post by papibe on 2012-11-11
Could you post the result of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig google.com
```Regards.

---

### Post by maembe on 2012-11-11
> **papibe said:**
> Could you post the result of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

dig google.com
```Regards.

ifconfig:
> eth0      Link encap:Ethernet  HWaddr 60:eb:69:bc:e1:74 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:656704 (656.7 KB)  TX bytes:656704 (656.7 KB)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:02:2e:21 
          inet addr:192.168.stuff  Bcast:192.168.stuff  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe02:2e21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:231763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:325828084 (325.8 MB)  TX bytes:17460372 (17.4 MB)

route -n:
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

nslookup
> Server:        127.0.0.1
Address:    127.0.0.1#53

Non-authoritative answer:
Name:    ubuntu.com
Address: 91.189.94.15

dig
> ; <<>> DiG 9.8.1-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2687
;; flags: qr rd ra; QUERY: 1, ANSWER: 11, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.            IN    A

;; ANSWER SECTION:
google.com.        300    IN    A    74.125.225.96
google.com.        300    IN    A    74.125.225.110
google.com.        300    IN    A    74.125.225.99
google.com.        300    IN    A    74.125.225.98
google.com.        300    IN    A    74.125.225.104
google.com.        300    IN    A    74.125.225.103
google.com.        300    IN    A    74.125.225.101
google.com.        300    IN    A    74.125.225.100
google.com.        300    IN    A    74.125.225.102
google.com.        300    IN    A    74.125.225.97
google.com.        300    IN    A    74.125.225.105

;; Query time: 430 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Nov 11 20:58:49 2012
;; MSG SIZE  rcvd: 204


---

### Post by papibe on 2012-11-12
If your IP is in the 192.68.2.* range, then your settings look OK.

Your DNS seem to be a bit slow. Could you post the result of these commands:
```
grep dnsmasq /etc/NetworkManager/NetworkManager.conf

cat /var/run/nm-dns-dnsmasq.conf
```Regards.

---

### Post by maembe on 2012-11-13
> **papibe said:**
> If your IP is in the 192.68.2.* range, then your settings look OK.

Your DNS seem to be a bit slow. Could you post the result of these commands:
```
grep dnsmasq /etc/NetworkManager/NetworkManager.conf

cat /var/run/nm-dns-dnsmasq.conf
```Regards.

My public ip is 75.168.**.***

grep dnsmasq /etc/NetworkManager/NetworkManager.conf
```
dns=dnsmasq
```

cat /var/run/nm-dns-dnsmasq.conf:
```

server=8.8.8.8
server=8.8.4.4
```

---

### Post by maembe on 2012-11-14
Here's an example of an error I get when I try to log in to Facebook:
No data received
Unable to load the web page because the server sent no data.

Not sure if this is helpful or not...

---

### Post by maembe on 2012-11-17
> **ahallubuntu said:**
> OK.  One thing to check: is the subnet used by the router different from the subnet used by the DSL modem?

What I mean is: if the router's LAN IP is 192.168.1.1 (and you get 192.168.1.X when connecting to it), is the DSL modem's IP the same 192.168.1.1?  Or is it different?  It should be different. (Change one of them to 192.168.2.1 or something like that.)  It could be this was not an issue when you had cable.

Or is your wireless router setup as an "access point" not as a router?

Try this: unplug your router temporarily from your DSL modem, and wire your computer directly to the modem.  In Ubuntu type "ifconfig" in a terminal and see what IP you get.  (Or ipconfig in Windows in a DOS window.)  (For privacy reasons, if you don't get 192.168.something or don't get 10.something, blot out the last digit of your IP.)

Now (with router still unplugged from modem) wire directly into your router into one of the LAN ports.  Repeat above.  What IP do you get?

In any case: did you re-configure the router after moving from cable to DSL?  Or did you use it as-is?  The subnet thing could be one explanation for the issues you are having.


Connected to modem:
IPv4: 192.168.0.X

Connected to router:
IPv4: 192.168.2.X

I just used the router as-is, without doing an sort of reconfiguration.

---

### Post by papibe on 2012-11-17
> **maembe said:**
> Connected to modem:
IPv4: 192.168.0.X

Connected to router:
IPv4: 192.168.2.X

I just used the router as-is, without doing an sort of reconfiguration.

That doesn't look right.

My guess now is that what you called a modem it is actually a router, and you have a double NAT problem (2 routers translating IP addresses in a row).

Usually, ISPs that provides DSL, like AT&T, give you a full working modem/router. In other words, a device that both connect you to your ISP account, get a public IP, and provides NAT for your home LAN.

Regards.

---

### Post by maembe on 2012-11-17
> **papibe said:**
> That doesn't look right.

My guess now is that what you called a modem it is actually a router, and you have a double NAT problem (2 routers translating IP addresses in a row).

Usually, ISPs that provides DSL, like AT&T, give you a full working modem/router. In other words, a device that both connect you to your ISP account, get a public IP, and provides NAT for your home LAN.

Regards.

I already had a router, because I previously had cable, so I bought a new DSL compatible modem, it isn't a modem/router combo or anything like that.

---

### Post by maembe on 2012-11-18
I just tried wiring directly in to the modem and everything worked like a champ.  Then, I wired in to the router and was running in to the same issues, so it pretty clearly has something to do with the router, although I have no idea what.

---

### Post by papibe on 2012-11-18
Could you post the brand name and model of the 2 devices?

Regards.

---

### Post by maembe on 2012-11-21
> **papibe said:**
> Could you post the brand name and model of the 2 devices?

Regards.

Modem: [http://www.bestbuy.com/site/NETGEAR/NETGEAR-DSL-%26-Cable-Modems-and-Gateways/pcmcat257000050025.c?id=pcmcat257000050025](http://www.bestbuy.com/site/NETGEAR/NETGEAR-DSL-%26-Cable-Modems-and-Gateways/pcmcat257000050025.c?id=pcmcat257000050025)

Router:  [http://www.bestbuy.com/site/Belkin+-+N300+Wireless-N+Router+with+4-Port+Switch/2089255.p?id=1218308699878&skuId=2089255](http://www.bestbuy.com/site/Belkin+-+N300+Wireless-N+Router+with+4-Port+Switch/2089255.p?id=1218308699878&skuId=2089255)

---

### Post by papibe on 2012-11-21
Thanks.

Your Netgear modem is a very curious device.

It is advertised as a modem, but it does NAT, and has a router mode.

From post #13, I can tell that the NAT is enabled, thus producing a double NAT conflict with your Belkin router.

While connected directly to your modem,  you can get to its admin page, and configure it as you want. I'd start disabling NAT, and reading more about the other functions. Here's the [PDF manual]("http://www.google.com/url?sa=t&rct=j&q=NETGEAR+-+Broadband+ADSL2%2B+Modem&source=web&cd=1&cad=rja&ved=0CDgQFjAA&url=http%3A%2F%2Fwww.downloads.netgear.com%2Ffiles%2FDM111PSPv2%2FDM111PSPv2_UM_8Aug11.pdf&ei=rEetUJ3QGIezqQH4o4GoDg&usg=AFQjCNFHVR3TWpsLqCK_kLd_4RTLBKRsug").

Hope that helps.
Regards.

---

### Post by maembe on 2012-11-24
> **papibe said:**
> Thanks.

Your Netgear modem is a very curious device.

It is advertised as a modem, but it does NAT, and has a router mode.

From post #13, I can tell that the NAT is enabled, thus producing a double NAT conflict with your Belkin router.

While connected directly to your modem,  you can get to its admin page, and configure it as you want. I'd start disabling NAT, and reading more about the other functions. Here's the [PDF manual]("http://www.google.com/url?sa=t&rct=j&q=NETGEAR+-+Broadband+ADSL2%2B+Modem&source=web&cd=1&cad=rja&ved=0CDgQFjAA&url=http%3A%2F%2Fwww.downloads.netgear.com%2Ffiles%2FDM111PSPv2%2FDM111PSPv2_UM_8Aug11.pdf&ei=rEetUJ3QGIezqQH4o4GoDg&usg=AFQjCNFHVR3TWpsLqCK_kLd_4RTLBKRsug").

Hope that helps.
Regards.

I tried disabling NAT, but that made the internet no longer work.  Looking through the docs I found this:  > Disabling NAT reboots the broadband ADSL2+ modem and resets its configuration settings to the factory defaults. 
Disable NAT only if you plan to set up the broadband ADSL2+ modem in a setting where you will be manually 
administering the IP address space on the LAN side of the modem

Do I need to do something with the LAN settings?

---

### Post by maembe on 2012-11-25
I changed one of the settings on the router to "use as an access point."  This seemed to solve the issues I was having.

Thanks for all of your help!

---

### Post by papibe on 2012-11-25
:o Ohh!

Glad you finally got it working.

Regards.

---

