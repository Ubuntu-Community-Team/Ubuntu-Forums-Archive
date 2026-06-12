---
title: "Change source IP regularly"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by conradin on 2013-04-07
Hi all, 
I just installed squid, so that I can change my outgoing IP.
heres where I have been reading:
[http://www.cyberciti.biz/faq/linux-unix-bsd-squid-proxy-set-tcp_outgoing_address/](http://www.cyberciti.biz/faq/linux-unix-bsd-squid-proxy-set-tcp_outgoing_address/)

instead of squid I use squid3 for the commands, since that's the version installed.

but I dont want to edit /etc/squid3/squid.conf
every time I want to change my outgoing IP. I would rather have my outgoing IP change based on a timer, or based on some scritpable CLI command.
so then i tried this:
```

~$ sudo squid3 tcp_outgoing_address 1.2.3.4
~$ sudo squid3 -k reconfigure
~$ sudo service squid3 restart
squid3 start/running, process 23891

``` 

(passing squid3 the tcp_outgoing_address as an argument with and ip similar format to the config file. CLI doesnt barf.
reconfigure, to set the changes, and restart the service to be sure....)
I expected it to work, since it didn't baulk about formatting, or whatever. But it doesn't seem to make a difference.
 
Does anyone know how i can set up this proxy to change my IP systemically?

---

### Post by sanderj on 2013-04-07
You can only change the outgoing IP address to an IP address that is on your interfaces. So check with "ifconfig" which IP address you have.

If you're behind NAT, things are different.

And on a typical home Internet connection, you only have one public IP address, so you can't change it.

---

