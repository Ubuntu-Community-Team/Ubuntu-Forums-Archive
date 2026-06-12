---
title: "Bandwidth Measurement inside a VM"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by james.walmsley on 2009-02-03
Hi all.

I have run the command
```

ifconfig

```

This shows the total data in and out of all of the network interfaces. The problem is I'm using a virtual machine (as in inside), and this value appears to be a aggregate for all other virtual machines on the actual physical hardware. 

I've tried to use iptables to show bandwidth usage, but it seems that ufw has added entries, so I can't get any sensible values from it.

All I want is number of MB uploaded from my IP to any IP and the number of MB downloaded from any any IP to my IP.

If I can get this value using iptables, I'd be happy, as I don't really want to run any special daemons.

I followed this guide:
[http://www.linux.com/articles/50649](http://www.linux.com/articles/50649)

But the values I get are always 0, because of some ufw-before-output etc chains.

Maybe the values on those chains are what I need.

James

---

### Post by james.walmsley on 2009-02-03
Update:

bandwidthd is the solution. It makes nice graphs and shows all the IP's on the specified subnets plus their usage.

```
apt-get install bandwidthd
```

Then simply create a symbolic link into your web-path (if apache or lighttpd is running)

```
ln -s /var/lib/bandwidthd/htdocs /var/www/bandwidth
```

Now opening a web-browser to:

http://<your-server-ip>/bandwidth/

Will show a nice display with graphs etc of the amount of bandwidth being eaten up by various hosts on the network.

It may even just show your own IP depending on your network topology.

James

---

