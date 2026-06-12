---
title: "resolv.conf keeps old configurations"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by pamiller3 on 2012-10-09
I have been searching for this answer for awhile and came up with nothing.  I recently upgraded from ubuntu 10.04 to 12.04 and I understand the auto config of the resolv.conf file and I have edited the /network/interface to include the changes but it keeps old configurations from when it was 10.04.

EXAMPLE:
network/interface=

auto eth0
iface eth0 inet static
        address <IP_ADDRESS>
        netmask 255.255.255.0
        gateway <IP_ADDRESS>
        network <IP_ADDRESS>
        broadcast <IP_ADDRESS>

dns-search <NEW_DOMAIN>
dns-domain <NEW_DOMAIN>
dns-nameservers <NEW_IP_ADDRESS> 4.2.2.1 8.8.8.8

I look into the /resolv.conf and it shows this:

nameserver <NEW_IP_ADDRESS>
nameserver 4.2.2.1
nameserver 8.8.8.8
search <NEW_DOMAIN>
domain <OLD_DOMAIN>
search <OLD_DOMAIN>
nameserver <OLD_IP_ADDRESS>
nameserver 4.2.2.1
nameserver 4.2.2.2

Any suggestions would be great

---

### Post by Karlchen on 2012-10-09
Hello, pamiller3.

Automatically updating resolv.conf will work on Ubuntu 12.04 only in case resolv.conf itself is located in the folder /run/resolvconf. The folder /etc has got to hold a symbolic link to /run/resolvconf/resolv.conf.
```
karl@ubuntu12 /etc $ ls -l resolv.conf
lrwxrwxrwx 1 root root 27 Aug  5 13:43 resolv.conf -> /run/resolvconf/resolv.conf
karl@ubuntu12 /etc $ 
```Kind regards,
Karl

---

### Post by pamiller3 on 2012-10-09
Alright I made the changes and removed the old configurations out of the /run/resolvconf/resolv.conf and then did an interface restart and it still shows the old configurations

---

### Post by steeldriver on 2012-10-09
Hi I *think* that when you do a dist-upgrade from a release that pre-dates the resolvconf service, your old manual DNS config gets saved to one of the files in /etc/resolvconf/resolv.conf.d/ (either /etc/resolvconf/resolv.conf.d/original or /base - not sure) and then appended to the dynamically generated /etc/resolv.conf file - maybe look in there and see if you can find the old entries?

See here:-   [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by pamiller3 on 2012-10-09
That seems to have worked, I eliminated the contents of the /etc/resolvconf/resolv.conf.d/original file and it worked.  Thanks for that.

A follow up is I am trying to add the line dns-domain in the network/interface file and when I do that it does not add that to the resolv.conf file.  Is there anyway that I can make sure that this server is added to the domain?

---

### Post by steeldriver on 2012-10-09
sorry I'm not familiar with a dns-domain field - I've only seen dns-nameservers and dns-search

---

### Post by pamiller3 on 2012-10-11
Alright I maybe barking up the wrong tree, I found that command on a blog...or forum..or somewhere around the inet.

Is there an easy command to confirm the hostname is part of the domain.  For example: hostname.domain.com

Thanks so much for the help

---

### Post by steeldriver on 2012-10-11
not sure exactly what you are looking for - in a general context you can get the host's fqdn using

```
hostname -f
```

but that's not exactly related to your /etc/network/interfaces DNS settings

---

### Post by jdthood on 2012-10-29
> **pamiller3 said:**
> That seems to have worked, I eliminated the contents of the /etc/resolvconf/resolv.conf.d/original file and it worked.  Thanks for that.

A follow up is I am trying to add the line dns-domain in the network/interface file and when I do that it does not add that to the resolv.conf file.  Is there anyway that I can make sure that this server is added to the domain?

The more correct thing to do would have been to eliminate the symlink /etc/resolvconf/resolv.conf.d/tail -> original and replace it by /etc/resolvconf/resolv.conf.d/tail -> /dev/null. But emptying  /etc/resolvconf/resolv.conf.d/original works just as well.

---

### Post by jdthood on 2012-10-29
> **pamiller3 said:**
> A follow up is I am trying to add the line dns-domain in the network/interface file and when I do that it does not add that to the resolv.conf file.  Is there anyway that I can make sure that this server is added to the domain?

Resolvconf only ever adds a "search" line to resolv.conf, never a "domain" line. This is because "search" lines do everything "domain" lines do, but are more versatile. The glibc resolvconf only uses either "domain" or "search", not both. So "search" it is.

In /etc/network/interfaces the use of "dns-domain" options works (and is treated as synonymous with "dns-search") but is deprecated in favor of "dns-search" for the reason just given.

---

### Post by jdthood on 2012-10-29
> **pamiller3 said:**
> Is there an easy command to confirm the hostname is part of the domain.  For example: hostname.domain.com

To ensure that you can look up 'hostname.domain.com' in DNS, just run "host hostname.domain.com".

Was that your question?

If you were asking whether or not the hostname should include a domain name part, the answer is No. In Debian and Ubuntu, the system hostname is standardly just a short hostname and not a fully qualified domain name.

   $ hostname
   foohost
   $ hostname -f
   foohost

---

