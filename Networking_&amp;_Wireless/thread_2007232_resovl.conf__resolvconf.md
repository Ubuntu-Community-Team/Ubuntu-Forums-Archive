---
title: "resovl.conf / resolvconf"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by surfer on 2012-06-20
i'm a bit lost with the new resolv.conf handling in ubuntu. can someone please answer my questions?

1. there seems to be a package that both depends on resolvconf and dnsmasq (which is used for caching and as local nameserver). what is the name of that package?

2. what script creates the resolv.conf symlink (pointing to ../run/resolvconf/resolv.conf)? can i call that script manually?

3. on a FAI install of a client, i saw that tere is no /run/resolvconf/resolv.conf file (the directory exists). what script puts that file there?

4. are there more questions about the new resolv.conf handling i forgot to ask?

---

### Post by surfer on 2012-06-20
by the way: i'm talking about a server setup here; no window manager installed. so nm-tool or NetworkManager are no options.

---

### Post by surfer on 2012-06-24
bump...

on my desktop machine, i saw that the dnsmasq-base package is installed. but (as far as i see) without any init.d or upstart script.

ok, on the desktop it looks like the network manager is starting dnsmasq:
```
$ ps -elf | grep dns
4 S nobody    3730   993  0  80   0 -  8253 poll_s 14:12 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.0.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec

```
how would i achieve the same on a server?

or is there just no point in having such a setup on a server, as a server will very rarely change its networking environment?

---

### Post by steeldriver on 2012-06-24
I can't answer any of your questions but there's some general info on manually configuring here

[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

---

### Post by chili555 on 2012-06-24
> or is there just no point in having such a setup on a server, as a server will very rarely change its networking environment?I think there is no point in having such a setup on a server because the server is not typically recalling the IP address of [www.google.com](www.google.com), [www.ebay.com](www.ebay.com), [www.amazon.com](www.amazon.com), etc. Dnsmasq accepts DNS queries and  either  answers  them  from  a  small, local cache  or  forwards  them  to a real, recursive, DNS server. 

Other than periodic updates, I think a server just sits there and waits for an inquiry from the network and responds. 

If you are simply trying to set up DNS nameservers, I suggest you set them in /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8
```If you are trying to do something more complicated, I probably don't know the answer.

---

### Post by bab1 on 2012-06-24
> **surfer said:**
> i'm a bit lost with the new resolv.conf handling in ubuntu. can someone please answer my questions?

1. there seems to be a package that both depends on resolvconf and dnsmasq (which is used for caching and as local nameserver). what is the name of that package?

On desktops this is Network Manager.  On 12.04 Server there is no Network Manager but the package **resolvconf** is still installed.> 

2. what script creates the resolv.conf symlink (pointing to ../run/resolvconf/resolv.conf)? can i call that script manually?

3. on a FAI install of a client, i saw that tere is no /run/resolvconf/resolv.conf file (the directory exists). what script puts that file there?

4. are there more questions about the new resolv.conf handling i forgot to ask?

The **resolvconf** app creates the /etc/resolv.conf file dynamically.  It uses the data in the /etc/network/interfaces file (i.e.dns-nameservers) for the DNS name server IP addresses on a Ubuntu 12.04 Server with static IP addressing.

Note: there are other locations that can hold hooks to the information if using DHCP or other dynamic IP addressing.

From the **resolvconf** man page```
 Normally  resolvconf  is  run  only by hook scripts attached to network
       interface configurers such as pppd(8) (for  ppp  interfaces),  to  DHCP
       clients  such  as dhclient(8), to ifup(8) and ifdown, and to DNS caches
       such as dnsmasq(8) (for the loopback interface).   These  hook  scripts
       furnish  resolvconf  with  information about nameservers.  
```

---

### Post by SeijiSensei on 2012-06-25
I'm not a big fan of the new dnsmasq/resolvconf system on clients and would certainly not use it on servers.  I'd just use apt-get to purge both dnsmasq and resolvconf and write a static copy of /etc/resolv.conf.  Furthermore, you might want to run bind9 on a server; having dnsmasq around would just get in the way.

---

### Post by bab1 on 2012-06-25
> **SeijiSensei said:**
> I'm not a big fan of the new dnsmasq/resolvconf system on clients and would certainly not use it on servers.  I'd just use apt-get to purge both dnsmasq and resolvconf and write a static copy of /etc/resolv.conf.  Furthermore, you might want to run bind9 on a server; having dnsmasq around would just get in the way.

DNSmasq is used with Network Manager and as such is *not installed* with Ubuntu 12.04 Server.  I agree that the **resolvconf** package is not needed on the Server.  A static file (resolv.conf) is more reliable.

---

### Post by jdthood on 2012-10-30
> **surfer said:**
> i'm a bit lost with the new resolv.conf handling in ubuntu. can someone please answer my questions?

1. there seems to be a package that both depends on resolvconf and dnsmasq (which is used for caching and as local nameserver). what is the name of that package?

NetworkManager

> 2. what script creates the resolv.conf symlink (pointing to ../run/resolvconf/resolv.conf)? can i call that script manually?

It is created by the resolvconf package postinst.

You should not call this script manually.  Instead do

[FONT="Courier New"]   dpkg-reconfigure resolvconf
[/FONT]
> 3. on a FAI install of a client, i saw that tere is no /run/resolvconf/resolv.conf file (the directory exists). what script puts that file there?

/sbin/resolvconf does.

---

### Post by jdthood on 2012-10-30
> **bab1 said:**
> The **resolvconf** app creates the /etc/resolv.conf file dynamically.

Actually it writes /run/resolvconf/resolv.conf, to which /etc/resolv.conf is generally symlinked.

---

