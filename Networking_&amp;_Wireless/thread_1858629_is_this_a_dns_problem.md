---
title: "is this a dns problem?"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by dsula on 2011-10-12
I have a bunch of computers (windows and ubuntu) hooked to my router. When I log into the router I can see all the connected computers, I can see their IP and I can also see the name of the computers.

When using windows, I can access all other machines using their names (even ubuntu). When trying to do the same with ubuntu I have to use the IP number. I'm sure there's some simple service missing on the ubuntu machine that queries the router for the name of the machine. Can anybody help?


Thank you.

---

### Post by papibe on 2011-10-12
It sounds familiar.

Could you post the results of these commands on the Ubuntu machine?
```
$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Regards.

---

### Post by dave01945 on 2011-10-12
I think that is because windows uses WINS to resolve the names into addresses but linux uses dns and unless you have a local dns server you will need to enter the ip.

 you might be able to setup linux to use WINS i'm not sure you will have to look into it

Probably the easiest way would be to give them static ip's an enter them into /etc/hosts file

--edit--

this should explain how to setup WINS
[http://www.korokithakis.net/posts/how-to-resolve-hostnames-in-linux/](http://www.korokithakis.net/posts/how-to-resolve-hostnames-in-linux/)

---

### Post by dsula on 2011-10-12
```
dsula@tabasco:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:80:b6:61  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe80:b661/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2742 (2.7 KB)  TX bytes:7364 (7.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

dsula@tabasco:~$ 

dsula@tabasco:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
dsula@tabasco:~$ 

dsula@tabasco:~$ nslookup ubuntu.com
Server:		68.87.71.230
Address:	68.87.71.230#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156

dsula@tabasco:~$ 

dig ubuntu.com

; <<>> DiG 9.7.0-P1 <<>> ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37146
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;ubuntu.com.			IN	A

;; ANSWER SECTION:
ubuntu.com.		600	IN	A	91.189.94.156

;; Query time: 36 msec
;; SERVER: 68.87.71.230#53(68.87.71.230)
;; WHEN: Wed Oct 12 17:16:50 2011
;; MSG SIZE  rcvd: 44

dsula@tabasco:~$ 
```

And here's an example how it doesn't work:
```
dsula@tabasco:~$ host mesera
mesera has address 208.68.143.50
Host mesera not found: 3(NXDOMAIN)
dsula@tabasco:~$ 
```
'mesera' resolves to 208.68... instead the correct IP would be 192.168.1.104

---

### Post by capscrew on 2011-10-12
> **dave01945 said:**
> I think that is because windows uses WINS to resolve the names into addresses but linux uses dns and unless you have a local dns server you will need to enter the ip.

Close...but no cigar!  Windows shares (SMB/CIFS) uses NetBIOS to resolve names.  A WINS server can hold and map NetBIOS names to IP addresses.> 

 you might be able to setup linux to use WINS i'm not sure you will have to look into it
Samba does not need a WINS server to operate correctly.> 

Probably the easiest way would be to give them static ip's an enter them into /etc/hosts file

--edit--

this should explain how to setup WINS
[http://www.korokithakis.net/posts/how-to-resolve-hostnames-in-linux/](http://www.korokithakis.net/posts/how-to-resolve-hostnames-in-linux/)

Samba explicitly states that you should not use a WINS server for a simple LAN.

---

### Post by dsula on 2011-10-12
> **dave01945 said:**
> 
Probably the easiest way would be to give them static ip's an enter them into /etc/hosts file


Yeah, that's what I don't want to do. But I'll take a look at the WINS. However for me this has nothing to do with windows. Shouldn't the router distribute the names ? Granted I don't know that much about networking. Maybe the router only supports this WINS protocol?

I might add: I also cannot connect from ubuntu to another ubuntu by name. So there's defenitly no windows involved here.

---

### Post by capscrew on 2011-10-12
> **dsula said:**
> I have a bunch of computers (windows and ubuntu) hooked to my router. When I log into the router I can see all the connected computers, I can see their IP and I can also see the name of the computers.

When using windows, I can access all other machines using their names (even ubuntu). When trying to do the same with ubuntu I have to use the IP number. I'm sure there's some simple service missing on the ubuntu machine that queries the router for the name of the machine. Can anybody help?


Thank you.

How are you trying to access these windows machines?  Are you using Nautilus to browse the shares?  Or...Are you trying to mount these shares to the local filesystem?

---

### Post by dsula on 2011-10-12
> **capscrew said:**
> How are you trying to access these windows machines?  Are you using Nautilus to browse the shares?  Or...Are you trying to mount these shares to the local filesystem?

It has nothing to do with windows. From any ubuntu machine I try to do
```
ping <host>
```
whereas <host> can be the name of another windows or ubuntu machine. The hostname gets resolved to  a wrong IP (see example in post above). If  I perform explicit ping <IP> all works fine.
When doing the same ping <host> in windows, all hostnames are reolved correctly (to other windows or other ubuntu).

---

### Post by capscrew on 2011-10-12
> **dsula said:**
> It has nothing to do with windows. From any ubuntu machine I try to do
```
ping <host>
```
whereas <host> can be the name of another windows or ubuntu machine. The hostname gets resolved to  a wrong IP (see example in post above). If  I perform explicit ping <IP> all works fine.
When doing the same ping <host> in windows, all hostnames are reolved correctly (to other windows or other ubuntu).

Ahhhhh...  Then for sure WINS or NetBIOS has nothing to do with this.  Your problem is you have no DNS resolution on the LAN side of your network.  This is why an Internet address (ubuntu.com) resolves, but a local address (192.168.etc) is redirected (by the router) and fails.

As stated above you can add all the IP to hostname mapping in the Ubuntu machines /etc/hosts file if the IP addresses are set to static (non-changing).  The /etc/hosts file is not dynamic; it needs to be manually configured.

The only other thing is to see if your router will handle the local DNS services.  Mine does.

Edit:  The address you mentioned is an Internet address owned by:```
OrgName:        FAST Search & Transfer Inc
OrgId:          FST-20
Address:        117 Kendrick Street
City:           Needham
StateProv:      MA
PostalCode:     02494
Country:        US

```

---

### Post by dsula on 2011-10-12
> **capscrew said:**
> Ahhhhh...  Then for sure WINS or NetBIOS has nothing to do with this.  Your problem is you have no DNS resolution on the LAN side of your network.  This is why an Internet address (ubuntu.com) resolves, but a local address (192.168.etc) is redirected (by the router) and fails.

As stated above you can add all the IP to hostname mapping in the Ubuntu machines /etc/hosts file if the IP addresses are set to static (non-changing).  The /etc/hosts file is not dynamic; it needs to be manually configured.

The only other thing is to see if your router will handle the local DNS services.  Mine does.

Well ok, I can understand that. But why is Windows able to resolve the hostnames? It still has to get the names from the router somehow, right? So I can assume that ubuntu would be able to get the same information, too, correclty configured.

---

### Post by capscrew on 2011-10-12
> **dsula said:**
> Well ok, I can understand that. But why is Windows able to resolve the hostnames? It still has to get the names from the router somehow, right? So I can assume that ubuntu would be able to get the same information, too, correclty configured.

Maybe.  I can't see the windows setups.  Can you provide that information.  I wouldn't assume anything.

On the Ubuntu host; What do you have in the /etc/resolv.conf file?  Are you using Network Manager to configure your interfaces by any chance?

Does the router have a DNS server server for the LAN?

---

### Post by dsula on 2011-10-12
Sure thing installing that WINS solved the problem.

Thanks all for the help. Just wondering why this is not installed by default. Do I have such a weird network that I'm the only one with this issue?

---

### Post by papibe on 2011-10-12
EDIT: Oops... I'm too slow to write.

Thanks for posting those results.

The problems lies in the fact that your router (192.168.1.1) is not set (or is not able) to work as your DNS in your LAN. Through DHCP, your server is setting an external server to work as your DNS router (68.87.71.230).

The problem with that configuration is that the machines in your network won't know each other, unless they use some sort of independent broadcast system.

Ubuntu uses the avahi services ([zero configuration networking]("http://en.wikipedia.org/wiki/Zero_configuration_networking")). That way you can access another Ubuntu machine using the domain .local (for example mesera.local).

As capscrew mentioned it, Windows machine use NETBIOS. My guess is that you are using SAMBA, then a process called nmbd is running and broadcasting Ubuntu's name in a language that Windows can understand.

The simplest solution would be research how to set your router to work as a DNS (or relay the requests). If that's not possible, there are a few alternatives.

Another way would be(hardworking solution) set all machines to use an static IP, and then write that information on each machine's hosts file. If you have a couple of machines in your network, this could be a practical solution. Personally, I wouldn't do it that way, because it feels like an administrator's nightmare.

Another solution is to change the way the Ubuntu machines resolve addresses. That rules are set on the file /etc/nsswitch.conf. You can set that before going to the DNS, Ubuntu use a table of listened broadcasts from NETBIOS. Here's a simple [tutorial]("http://ubuntuforums.org/showthread.php?t=88206") on how to accomplish that.

I hope this helps,
Regards.

---

### Post by capscrew on 2011-10-12
> **dsula said:**
> Sure thing installing that WINS solved the problem.

Thanks all for the help. Just wondering why this is not installed by default. Do I have such a weird network that I'm the only one with this issue?

If you installed using the blog post mentioned by dave01945, you will have problems down the road.  This is not a long term viable way to resolve hostnames in a Ubuntu/Windows environment.  Good luck.

---

### Post by capscrew on 2011-10-12
> **papibe said:**
> EDIT: Oops... I'm too slow to write.


Another solution is to change the way the Ubuntu machines resolve addresses. That rules are set on the file /etc/nsswitch.conf. You can set that before going to the DNS, Ubuntu use a table of listened broadcasts from NETBIOS. Here's a simple [tutorial]("http://ubuntuforums.org/showthread.php?t=88206") on how to accomplish that.

I hope this helps,
Regards.

This tutorial is from 2005.  It also is incorrect for what we are talking about here.  Neither WINS (Windows Internet Server) nor Winbind (the mapping of Windows NT users to linux users) is applicable in this context.

Edit:  As soon as the DNS cache is exhausted the OP will have problems resolving Internet DNS names.  The resolve routines will hang looking for a WINS server that holds true Internet DNS names.

---

### Post by dsula on 2011-10-12
> **capscrew said:**
> If you installed using the blog post mentioned by dave01945, you will have problems down the road.  This is not a long term viable way to resolve hostnames in a Ubuntu/Windows environment.  Good luck.


```
more /etc/resolv.conf 
# Generated by NetworkManager
nameserver 68.87.71.230
nameserver 68.87.73.246
dsula@tabasco:~$ ^C

```

The router has its DNS server disabled. I don't want to enable it because it requires one to manually enter the names and the IP it resolves to. That's what I want to avoid. I don't want to have to enter a fixed IP somewhere. It's a linksys RV082, I call it a mid-range home-network router.

In my system frequently new people with all kinds of machines arrive and connect to the network. I need to be able to easily access all computers by name.

So to summarize this is what I understand:
1. ubuntu requires a local DNS server to do the job right.
2. windows does the same thing using some sort of magic
3. solution: install DNS server, or static host IP list
4. .. or WINBIND which will give me some issues sometimes.

Hmmm... and I always thought ubuntu in its version 10 is plug'n play easy....

---

### Post by capscrew on 2011-10-12
> **dsula said:**
> ```
more /etc/resolv.conf 
# Generated by NetworkManager
nameserver 68.87.71.230
nameserver 68.87.73.246
dsula@tabasco:~$ ^C

```

The router has its DNS server disabled. I don't want to enable it because it requires one to manually enter the names and the IP it resolves to. That's what I want to avoid. I don't want to have to enter a fixed IP somewhere. It's a linksys RV082, I call it a mid-range home-network router.

In my system frequently new people with all kinds of machines arrive and connect to the network. I need to be able to easily access all computers by name.

So to summarize this is what I understand:
1. ubuntu requires a local DNS server to do the job right.
2. windows does the same thing using some sort of magic
3. solution: install DNS server, or static host IP list
4. .. or WINBIND which will give me some issues sometimes.

Hmmm... and I always thought ubuntu in its version 10 is plug'n play easy....

Windows does DNS resolution the same as Ubuntu; by using the DNS (Domain Name System) protocol.

It may be that Windows is configured differently than Ubuntu to resolve private addressing (192.168.etc or others) but it still uses the same DNS protocol

Ubuntu (all distros really) have always needed LAN side DNS or /etc/hosts to set up to resolve hosts.  Lately AVAHI has brought  zeroconf to Ubuntu.  With your present setup I can't tell you haw to test, but on a normally configured host you might try ping <hostname>.local.  @papibe mentioned it above.

Edit:  Winbind (Samba's winbindd) will ALWAYS give you problems.

Since you have Samba installed; I believe it was installed when you installed winbindd, you might as well resolve everything to NetBIOS names if all you want is a mapping of IP address to <some_name>.  Are all of the other guests that you have using Windows?

---

### Post by dsula on 2011-10-12
> **capscrew said:**
> 

Edit:  Winbind (Samba's winbindd) will ALWAYS give you problems.

What kind of problems can I expect?

---

### Post by capscrew on 2011-10-12
> **dsula said:**
> What kind of problems can I expect?

Internet (public) DNS problems.  As I said before; As soon as the DNS cache is exhausted the you will have problems resolving Internet DNS names. The resolve routines will hang at the WINS server looking for DNS names.  WINS can't resolve DNS names only NETBIOS.

Now that I think of it; did you setup a WINS server?  On which host does it reside?

---

### Post by SeijiSensei on 2011-10-12
Many routers will build the DNS server entries for you dynamically if the client machines get their addresses from the router via dhcp.  I'd suggest turning on the router's DNS server and see what happens. Don't bother making any entries in any tables to start with.  My guess is those entries are only needed for machines that have static IPs.

As to your broader question about name resolution, that's more complex.  *nix machines use the Domain Name Service for server-based resolution, which requires that some machine on the network be configured as a DNS server.  Windows uses a variety of methods to resolve names depending on the version of Windows and whether it resides in a Windows "domain" with an Active Directory server.

In the simplest case of some Windows machines sharing a network subnet, the machines broadcast their names using the "NetBIOS" protocol.  The other machines build a database of host/IP pairings from these broadcasts.  A step up from that is WINS, where a server on the network is assigned the responsibility of collating these broadcasts and building the database of pairings.  [Samba]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html") functions excellently as a WINS server; I've used it as the WINS primary in networks composed mostly of Windows clients.  Windows versions starting with XP prefer to use DNS like *nix machines do.  In a network with an AD server, that machine builds the database of pairings and provides it via DNS just like a Linux machine running BIND would.

It's possible to use [ISC DHCP]("http://www.isc.org/software/dhcp") and [ISC BIND]("http://www.isc.org/software/bind") together to provide a [dynamic DNS server]("http://www.debian-administration.org/article/Configuring_Dynamic_DNS__DHCP_on_Debian_Stable").  [dnsmasq]("https://help.ubuntu.com/community/Dnsmasq") is another alternative that's generally regarded as easier to configure, though I've not used it.

If your router is running DD-WRT, or can be flashed to use DD-WRT, it [supports dnsmasq by default]("http://www.dd-wrt.com/wiki/index.php/DNSMasq_as_DHCP_server").

---

### Post by greenrider on 2011-10-17
I see this behavior-- the thing that concerns me is not that host names do not resolve, it's that every "unknown" host name I try to ping appears to somehow be resolving to that same IP address that other(s) have mentioned above.  My windows machines on the same network do not do this, but my Ubuntu machines do.   (I have both Ubuntu 10.x and 11.x machines, and they all do this).

Anybody know why this particular address keeps showing up?  It's a bit concerning from a security standpoint.  (who knows what traffic is being directed to that IP?)


ubuntu@ubuntu:~$ **ping copernicus**
PING copernicus ([COLOR=Red]208.68.143.50[/COLOR]) 56(84) bytes of data.
^C
--- copernicus ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms

ubuntu@ubuntu:~$ **ping oogaboogaonetime**
PING oogaboogaonetime ([COLOR=Red]208.68.143.50[/COLOR]) 56(84) bytes of data.
^C
--- oogaboogaonetime ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4032ms

ubuntu@ubuntu:~$ **whois [COLOR=Red]208.68.143.50[/COLOR]**
#
# Query terms are ambiguous.  The query is assumed to be:
#     "n 208.68.143.50"
#
# Use "?" to get help.
#

#
# The following results may also be obtained via:
# [http://whois.arin.net/rest/nets;q=208.68.143.50?showDetails=true&showARIN=false&ext=netref2](http://whois.arin.net/rest/nets;q=208.68.143.50?showDetails=true&showARIN=false&ext=netref2)
#

NetRange:       208.68.136.0 - 208.68.143.255
CIDR:           208.68.136.0/21
OriginAS:       AS40066
NetName:        FAST-GNS
NetHandle:      NET-208-68-136-0-1
Parent:         NET-208-0-0-0-0
NetType:        Direct Assignment
RegDate:        2006-06-28
Updated:        2011-03-16
Ref:            [http://whois.arin.net/rest/net/NET-208-68-136-0-1](http://whois.arin.net/rest/net/NET-208-68-136-0-1)
[COLOR=Red]
OrgName:        FAST Search & Transfer Inc[/COLOR]
OrgId:          FST-20
Address:        117 Kendrick Street
City:           Needham
StateProv:      MA

---

### Post by papibe on 2011-10-17
Hi greenrider. Welcome to the forums.

Although further tests and info would be needed, that looks like a classic case of 'NXDOMAIN hijacking'.

I recommend that you create your own thread to gain more attention and focus to your problem.

Regards.

---

### Post by capscrew on 2011-10-17
> **greenrider said:**
> I see this behavior-- the thing that concerns me is not that host names do not resolve, it's that every "unknown" host name I try to ping appears to somehow be resolving to that same IP address that other(s) have mentioned above.  My windows machines on the same network do not do this, but my Ubuntu machines do.   (I have both Ubuntu 10.x and 11.x machines, and they all do this).

Anybody know why this particular address keeps showing up?  It's a bit concerning from a security standpoint.  (who knows what traffic is being directed to that IP?)


ubuntu@ubuntu:~$ **ping copernicus**
PING copernicus ([COLOR=Red]208.68.143.50[/COLOR]) 56(84) bytes of data.
^C
--- copernicus ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3023ms

ubuntu@ubuntu:~$ **ping oogaboogaonetime**
PING oogaboogaonetime ([COLOR=Red]208.68.143.50[/COLOR]) 56(84) bytes of data.
^C
--- oogaboogaonetime ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4032ms

ubuntu@ubuntu:~$ **whois [COLOR=Red]208.68.143.50[/COLOR]**
#
# Query terms are ambiguous.  The query is assumed to be:
#     "n 208.68.143.50"
#
# Use "?" to get help.
#

#
# The following results may also be obtained via:
# [http://whois.arin.net/rest/nets;q=208.68.143.50?showDetails=true&showARIN=false&ext=netref2](http://whois.arin.net/rest/nets;q=208.68.143.50?showDetails=true&showARIN=false&ext=netref2)
#

NetRange:       208.68.136.0 - 208.68.143.255
CIDR:           208.68.136.0/21
OriginAS:       AS40066
NetName:        FAST-GNS
NetHandle:      NET-208-68-136-0-1
Parent:         NET-208-0-0-0-0
NetType:        Direct Assignment
RegDate:        2006-06-28
Updated:        2011-03-16
Ref:            [http://whois.arin.net/rest/net/NET-208-68-136-0-1](http://whois.arin.net/rest/net/NET-208-68-136-0-1)
[COLOR=Red]
OrgName:        FAST Search & Transfer Inc[/COLOR]
OrgId:          FST-20
Address:        117 Kendrick Street
City:           Needham
StateProv:      MA

The answer is fully explained [**_[COLOR="Blue"]here[/COLOR]_**]("http://dbhovel.com/Blog/category/networking.aspx") and [**_[COLOR="Blue"]here[/COLOR]_**]("http://forums.fedoraforum.org/showthread.php?t=257161") and [**_[COLOR="Blue"]here[/COLOR]_**]("http://blog.cuviper.com/2011/07/23/dnsmasq-comcast-vpn/").

I believe your ISP (Comcast?) is redirecting anything it can't resolve to that address.  See if all your hosts have the same DNS servers listed in their configuration files.  I would configure your DNS servers to be 8.8.8.8 amd 8.8.4.4.  These are owned by Google and are know to resolve properly.

---

### Post by greenrider on 2011-10-20
Wow, thank you. And No thank you com cast! I'm not happy at all and will def be changing that.  I was trying to vnc and rdp and it was failing/ trying to connect to the mystery address for that too.  Not cool!  This rates right up there with com cast routing all my traffic to LA before getting on the Internet proper but thankfully they fixed that. Grr...

---

### Post by capscrew on 2011-10-20
> **greenrider said:**
> Wow, thank you. And No thank you com cast! I'm not happy at all and will def be changing that.  I was trying to vnc and rdp and it was failing/ trying to connect to the mystery address for that too.  Not cool!  

This is the primary reason I run a dns server on the local (LAN) side (in my router.  The only things I redirect are Internet traffic that I point to Google's DNS servers.> 

This rates right up there with com cast routing all my traffic to LA before getting on the Internet proper but thankfully they fixed that. Grr...
Actually this used to happen with telephony all the time.  It is because of peering arrangements.  I would be more interested in the number of hops and not where those hops were.

---

