---
title: "Permanent DNS for a DSL connection"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by shashanksingh on 2011-12-04
I have a DSL connection which I suppose refreshes the /etc/resolv.conf file each time it connects.

But sometimes the DNS of my ISP does not work.

Is there a way to permanently add a global DNS in the resolv.conf file, which will not be erased by Network Manager each time or any other way to add it?

---

### Post by fdrake on 2011-12-04
you can add it to the hosts list in /etc/hosts 
or
you can add the entry into "host"  line into /etc/nsswitch.conf 

check this link for help:[http://www.faqs.org/docs/securing/chap6sec71.html](http://www.faqs.org/docs/securing/chap6sec71.html)

I would put first the files path (/etc/hosts)  and then the DNS address in the host section:
"hosts:      file-path dns-addr "

---

### Post by shashanksingh on 2011-12-04
> **fdrake said:**
> you can add it to the hosts list in /etc/hosts 
or
you can add the entry into "host"  line into /etc/nsswitch.conf 

check this link for help:[http://www.faqs.org/docs/securing/chap6sec71.html](http://www.faqs.org/docs/securing/chap6sec71.html)

I would put first the files path (/etc/hosts)  and then the DNS address in the host section:
"hosts:      file-path dns-addr "

Im a little novice with this so please bear with me.

Heres what my hosts in nsswtich say


> hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

What I was thinking to do is to add a DNS server IP (like 8.8.8.8 ) which my machine looks onto if my ISP DNS is not working (which is often)

I know I can directly add mappings to the host file, like directly add the IP of google, or frequently used sites.

Can I add a nameserver in hosts?

---

### Post by fdrake on 2011-12-04
at first I thought you could just add the entry nameserver to /ets/host. but this is not the case , sorry!  thinking a little bit longer I don't think that's the way was supposed to work.

a possible solution that i found is

```
sudo gedit /etc/sysconfig/network-scripts/ifcfg-eth0
```
and chage the entry "PEERDNS=yes"  to "PEERDNS=no". this should stop NetworkManger from recreating the file.

restart and add the nemaserv to /etc/resolv.conf

---

### Post by shashanksingh on 2011-12-04
> **fdrake said:**
> at first I thought you could just add the entry nameserver to /ets/host. but this is not the case , sorry!  thinking a little bit longer I don't think that's the way was supposed to work.

a possible solution that i found is

```
sudo gedit /etc/sysconfig/network-scripts/ifcfg-eth0
```
and chage the entry "PEERDNS=yes"  to "PEERDNS=no". this should stop NetworkManger from recreating the file.

restart and add the nemaserv to /etc/resolv.conf

Im afraid no /etc/sysconfig in my system

---

### Post by fdrake on 2011-12-04
you are right ... I was working at the moment on fedora.
in ubuntu should be:

1-
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf

```
make sure you have these lines:
> 
[ifupdown]
managed=false



2-
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf

```
make sure you have those line in the file :
> 
auto eth0
iface eth0 inet dhcp


3- edit your /etc/resolv.conf file with your dns address

4-restart
```

sudo ifdown -a
sudo ipup -a

```

---

