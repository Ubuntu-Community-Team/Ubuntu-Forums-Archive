---
title: "A way to see what and where my notebook is connecting to?"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by Clear Obama on 2011-10-24
Previously I had assumed if I had firestarter running, I could see all internet connections coming in/going out. However, lately I've noticed the network activity applet in my panel has been showing steady streams of data coming in, but I couldn't find out what program is doing it or the IP of the source. 

When I was using Windows, I could just type "ipconfig" and up came a list of all network connections. Anything like this for Ubuntu? And if I do an existing connection, how can I quickly close it?

---

### Post by varunendra on 2011-10-27
> **Clear Obama said:**
> When I was using Windows, I could just type "ipconfig" and up came a list of all network connections. Anything like this for Ubuntu? And if I do an existing connection, how can I quickly close it?
Much better than ipconfig:
```
ifconfig -a
```(the -a switch is not necessary, it lists all connections - active or not)

To close an existing connection:
```
sudo ifdown <the logical name of interface seen in output of ifconfig here>
```To bring it up again, simply replace *ifdown* with *ifup*.

However, in order to monitor what is creating that traffic, you need something else I may not be aware of. Maybe a firewall application or something alike.


**_EDIT_:**
See if you can find something useful here: [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by Lars Noodén on 2011-10-27
[netstat](http://manpages.ubuntu.com/manpages/oneiric/en/man8/netstat.8.html) will show connections in and out.

---

### Post by haqking on 2011-10-27
> **Lars Noodén said:**
> [netstat](http://manpages.ubuntu.com/manpages/oneiric/en/man8/netstat.8.html) will show connections in and out.

+1

ipconfig in windows does not show your connection activity, it shows your network interface configuration similar to ifconfig in linux.


netstat works in linux and windows, and you would use netstat in windows also not ipconfig

you can also use one of many network monitoring tools such as wireshark if you want to really analyze your source/destination traffic

---

### Post by Clear Obama on 2011-11-06
Thanks for all the great suggestions. 

ifconfig tells me how much traffic lo, etho and usb0 are sending and receiving, but I'm looking for a way to list all the recent and current connections, preferably also identifying what programs are using them.

Netstat does that, but it also lists "unix" connections in addition to "tcp" connections.

Iptraf is good, but it don't show what's happening with usb0, which is what I mostly use for internet access these days.

Is there a firewall program that will alert me and request my permission to send or receive packets?

---

### Post by Lars Noodén on 2011-11-07
> **Clear Obama said:**
> Netstat does that, but it also lists "unix" connections in addition to "tcp" connections.

Take another look at [netstat](http://manpages.ubuntu.com/manpages/oneiric/en/man8/netstat.8.html).  You can have it show you just the TCP connections if you want.  

```

netstat -t

```

---

