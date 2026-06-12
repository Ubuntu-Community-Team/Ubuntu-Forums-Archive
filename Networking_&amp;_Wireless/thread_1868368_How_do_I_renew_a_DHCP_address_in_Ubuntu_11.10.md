---
title: "How do I renew a DHCP address in Ubuntu 11.10???"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by phil_ on 2011-10-24
How do I renew an IP address now upstart is involved?

```
root@server:~# dhclient eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
RTNETLINK answers: File exists

```

Sorry if its a basic question, but I've been searching around for at least hour and cannot find much info about this... 

I've tried to use this to help me understand it, [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

so I've checked /etc/init .. but there are no scripts which look like they could help me renew an IP address in there? Do I need to download / write one?

thanks in advance.

---

### Post by newbie-user on 2011-10-24
You can reload the ip address by typing "/etc/init.d/networking restart"

---

### Post by papibe on 2011-10-25
Just to add a little more detail information. If you are running a desktop edition, then network-manager is administrating your network settings. Thus the command to restart the network is:
```
sudo service network-manager restart
```
In the case you are using a server edition (or have uninstalled n-m) then the proper way is:
```
sudo service networking restart
```
Hope it helps,
Regards.

---

