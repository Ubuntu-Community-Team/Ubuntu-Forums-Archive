---
title: "Cannot get NetworkManager to prepend nameserver"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by frankvw on 2009-08-27
Hi, everyone,

I use the NetworkManager applet to set up a 3G connection using a USB modem, which works fine. However on the machine with the 3G modem I also run a name server to resolve domain names for internal use. This requires that /etc/resolv.conf contain the following line:

```
nameserver 127.0.0.1
```

and for a number of reasons I need this line to appear BEFORE the IP addresses of other name servers, so that the local DNS gets consulted before any external ones (which has a lot to do with messy workarounds, legacy issues and other complications that I won't bore you with at this time).

In this and other forums I have read that in order to do this, I must include a 'prepend' statement in /etc/dhcp3/dhclient.conf. I have done this, but it does not seem to have any effect.

My /etc/dhcp3/dhclient.conf file currently contains the following:

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
send host-name "<hostname>";
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```

I restarted the networking service and (even though this isn't Windows, but desperate times call for desperate measures) I even rebooted the system. To no avail; the reference to localhost as a name server in /etc/resolv/conf gets clobbered by NetworkManager every time.

Head, meet wall. Wall, meet head.

What am I overlooking? I've spent three evenings trying everything I could think of, but I'm stumped.

Any hints to steer me into the right direction would be appreciated!

Thanks!

// FvW

---

### Post by antero_h__ on 2010-06-29
The source of the problem is most likely that ppp client fails to respect the  prepend domain-name-servers line in dhclient.conf. The resolution should probably be included in some FAQ about PPP and dnsmasq (or similar local dns cache) (I found it in a debian bug), but because I had to (again) google this up when setting up a new Ubuntu (10.4 amd64) laptop and landed in this thread, here's the missing magic:

sudo apt-get install resolvconf

---

