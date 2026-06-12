---
title: "Mapping Hostnames When Using DHCP"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by Jack Waugh on 2011-07-23
I can do this:

```

$ hostname
jack-ntbk
$ ssh inspiron.local
Linux inspiron 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!

```
...

What configuration variables do I have to check on both machines to come to an understanding of why it is that when I cite "inspiron.local" as an argument to "ssh", I get connected to my other computer instead of an error message?  How is the mapping from host name to IP# happening?

The computers are connected via Ethernet (via a USB-to-Ethernet adaptor in the case of the Inspiron) to the LAN side of an ordinary home router (an SMC) that is configured to serve DHCP.

"jack-ntbk" was initialized from an Ubuntu Server 10.04.1 CD and then I loaded Lubuntu-desktop on it.

"inspiron" has no desktop software, just server.  I started dhclient on it manually, with no args.

---

### Post by papibe on 2011-07-23
That is the result of running the ['zero configuration network']("http://en.wikipedia.org/wiki/Zeroconf") tool named [avahi]("http://en.wikipedia.org/wiki/Avahi_%28software%29").

Probably your /etc/nsswitch.conf file has a line like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
That rules read something like this: to translate names into IPs first use files (basically /etc/hosts), then use avahi, then use your DNS (probably your router).

Is that help?
Regards.

---

### Post by Jack Waugh on 2011-07-24
Yes, papibe, your response is very helpful; thank you.

I suppose for avahi publication of hostnames to work, it has to be running on both machines: the one whose hostname I want to see, and the one from which I want to see it.

---

### Post by papibe on 2011-07-24
That is correct.

You can check if avahi is running by either running:
```
$ sudo service avahi-daemon status
```
o this:
```
$ ps aux | grep avahi
```
Regards.

---

