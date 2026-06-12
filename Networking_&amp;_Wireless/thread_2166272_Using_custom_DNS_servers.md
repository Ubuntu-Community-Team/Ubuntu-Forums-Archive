---
title: "Using custom DNS servers"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by jsvidyad on 2013-08-08
Hello,

    If I want my ubuntu 12.04 system to use some other DNS servers rather than the ones of my ISP, how do I set it up?

---

### Post by TheFu on 2013-08-08
On a desktop, the settings are in a GUI somewhere. Probably where you set the static IP.  Sorry I can't be more specific. I run servers and my desktop is actually a server install with LXDE added.

On a server, the settings are in /etc/network/interfaces  **man interfaces** explains.

---

### Post by chili555 on 2013-08-08
> **jsvidyad said:**
> Hello,

    If I want my ubuntu 12.04 system to use some other DNS servers rather than the ones of my ISP, how do I set it up?Right-click the Network Manager icon and select 'Edit Connections.' Select wired or wireless as appropriate and then IPv4 settings. Set it up as attached, save close and enjoy.

You may also be interested in this: [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/) It's in the repositories.

---

### Post by jsvidyad on 2013-08-09
Right now, running the command 
cat /etc/resolv.conf

shows the nameserver to be 127.0.0.1 . This is for a wired ethernet connection. This means that the nameserver is my computer itself. How can I find which DNS server is used for requests by that nameserver running on my computer?

---

### Post by chili555 on 2013-08-09
> **jsvidyad said:**
> Right now, running the command 
cat /etc/resolv.conf

shows the nameserver to be 127.0.0.1 . This is for a wired ethernet connection. This means that the nameserver is my computer itself. How can I find which DNS server is used for requests by that nameserver running on my computer?Actually, that means that DNS is handled by dnsmasq: [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)> A DNS server resolves human readable domain names into IP addresses. For example, when one requests ubuntu.com, the DNS server finds the IP address for ubuntu.com . One can run a DNS cache on a computer via the steps below. This will shorten the time required to look up domain names when browsing. The difference in time is on the order of hundreds of milliseconds. To learn what DNS nameservers are in use now, run:```
nm-tool
```In many cases, the DNS nameserver will be the router address, something like 192.168.0.1. That means that the router holds the actual DNS addresses supplied by your internet service provider. You can find these in the administration pages of the router. In this example, see DNS1 and DNS2. 

[http://irrigationcaddy.com/blog/wp-content/uploads/2011/04/router-external-IP-address21.jpg](http://irrigationcaddy.com/blog/wp-content/uploads/2011/04/router-external-IP-address21.jpg)

---

### Post by jsvidyad on 2013-08-14
> **chili555 said:**
> Actually, that means that DNS is handled by dnsmasq: [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)To learn what DNS nameservers are in use now, run:```
nm-tool
```In many cases, the DNS nameserver will be the router address, something like 192.168.0.1. That means that the router holds the actual DNS addresses supplied by your internet service provider. You can find these in the administration pages of the router. In this example, see DNS1 and DNS2. 

[http://irrigationcaddy.com/blog/wp-content/uploads/2011/04/router-external-IP-address21.jpg](http://irrigationcaddy.com/blog/wp-content/uploads/2011/04/router-external-IP-address21.jpg)

Hello,
   Thanks for the info. The url you provided for the dnsmasq mentions that dnsmasq interferes with network manager. So, if I want to use the wireless interface of a laptop to connect to a wireless network, will I have to uninstall dnsmasq ?

---

### Post by TheFu on 2013-08-14
When I run nm-tool, it doesn't work. Ubuntu 12.04 system.  
```
$ nm-tool
The program 'nm-tool' is currently not installed. ....
```

The way I know works on every system is to check the **/etc/resolv.conf** file or use **dig**.

```
$ dig google.com

; <<>> DiG 9.8.1-P1 <<>> google.com
.
.
.
;; Query time: 20 msec
;; **SERVER: 192.168.1.1#53(192.168.1.1)**
;; WHEN: Wed Aug 14 07:36:31 2013
;; MSG SIZE  rcvd: 124

```
See the "server" line above? THAT is the DNS server used.

---

### Post by chili555 on 2013-08-14
> **jsvidyad said:**
> Hello,
   Thanks for the info. The url you provided for the dnsmasq mentions that dnsmasq interferes with network manager. So, if I want to use the wireless interface of a laptop to connect to a wireless network, will I have to uninstall dnsmasq ?I don't think that's the case these days. They work together pretty seamlessly.

---

### Post by chili555 on 2013-08-14
> **TheFu said:**
> 
```
$ dig google.com

; <<>> DiG 9.8.1-P1 <<>> google.com
.
.
.
;; Query time: 20 msec
;; **SERVER: 192.168.1.1#53(192.168.1.1)**
;; WHEN: Wed Aug 14 07:36:31 2013
;; MSG SIZE  rcvd: 124

```
See the "server" line above? THAT is the DNS server used.Except that is the address of your router. I doubt it is an actual DNS nameserver, rather, it holds the actual addresses just like my and most routers. Please see attached.

---

### Post by TheFu on 2013-08-14
> **chili555 said:**
> Except that is the address of your router. I doubt it is an actual DNS nameserver, rather, it holds the actual addresses just like my and most routers. Please see attached.

It provides DNS for internal systems and acts like a cache for external lookups.  [http://www.howtogeek.com/69696/how-to-access-your-machines-using-dns-names-with-dd-wrt/](http://www.howtogeek.com/69696/how-to-access-your-machines-using-dns-names-with-dd-wrt/) shows how easy this is.  I have about 50 DHCP hosts with static IPs provided by the router and DNS is maintained for about 100 hosts.  No need to run Bind - BTW, I have run Bind in a corporate environment. Best to let the pros do that.

---

### Post by chili555 on 2013-08-14
>  I have about 50 DHCP hosts with static IPs provided by the router and DNS is maintained for about 100 hosts.Very interesting. The ordinary wireless poster is unlikely to have this sort of setup. If they do, they hardly need poor old Chili to fix up their DNS!

---

### Post by TheFu on 2013-08-14
> **chili555 said:**
> Very interesting. The ordinary wireless poster is unlikely to have this sort of setup. If they do, they hardly need poor old Chili to fix up their DNS!

VM sprawl is a *small* issue for me. ;)

The point is that running Bind on a home LAN just isn't necessary. Your router can do it for internal DNS needs. For external - definitely pay a real DNS service the $20/yr for expertise and security.

---

