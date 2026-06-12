---
title: "VPN and DNS resolution"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by mockdeep on 2010-10-15
So I've got what I think is a pretty simple problem, and so far I haven't had any luck finding a clear solution on the web, though there seems to be plenty of talk about it.

Basically, my job has a VPN.  They have a number of pages within that VPN that map to the .local domain.  They're mostly a mac shop, so they just drop the nameserver addresses into the file /etc/resolver/local and it picks that up and redirects appropriately.  Unfortunately for me, I haven't been able to discover a way to get access to the pages using Linux except by direct access through the IP address.  I have the VPN set up through the network manager and everything otherwise seems to be in order.

How can I set it up so that .local redirects using our nameservers?  I've been mucking about in the network manager and elsewhere all day with no luck.  Using Ubuntu 10.10 on a MacBook Pro.

---

### Post by SeijiSensei on 2010-10-15
If you have access to the list of hostname/IP mappings, you can place them in /etc/hosts on your machine and use the hostnames instead of IP addresses.  I don't know what the format of /etc/resolver/local looks like, but if it's a plain text file that you can read over the network, you could automatically update /etc/hosts with a bash script.  A little magic with awk should do the trick.

---

### Post by mockdeep on 2010-10-19
/etc/resolver/local just contains a couple of lines:

nameserver  one.ip.address
nameserver  another.ip.address

Basically, because it's in a file named 'local' it resolves all domains ending in 'local' using the nameservers in that file.  All others go through the regular routes.  I've seen where some people prepend /etc/resolv.conf with the addresses using a script whenever it changes, but I guess I was hoping there was some way to handle this that the network manager understands.  And then there's also the issue that those nameservers end up being checked to resolve all domains, though that may not be such a huge issue.

---

### Post by SeijiSensei on 2010-10-19
Is /etc/resolv.conf on the Linux machine a static file, or is it created each time by DHCP?  If the latter, you can edit /etc/dhcp3/dhclient.conf and remove domain-name and domain-name-servers from the request list.  Now, in either case, create an /etc/resolv.conf with those identical nameserver lines followed by the directive "search .local".  That will append .local to any unqualified hostname.

Is this a laptop or netbook that needs to resolve names when outside the building as well?  If so, you should add a couple of nameserver records for public DNS servers like Google's 4.4.4.4 and 8.8.8.8, your ISP's servers, or [OpenDNS]("http://www.opendns.com/start/").

Don't the nameserver assignments remain fixed for relatively long periods of time?  If so, you shouldn't need to edit this file very often. Perhaps the IP admins can place a copy of /etc/resolver/local in a place you can access over the network?  If it's on an internal webserver, you can set up a script to run periodically from cron that would use wget to retrieve the current resolver list and append the needed footer like this:

```
#!/bin/bash
cd /etc
cp resolv.conf resolv.conf.backup
rm -f resolv.new
wget http://path.to.some.webserver/local -O resolv.new
echo 'nameserver 4.4.4.4' >> resolv.new
echo 'nameserver 8.8.8.8' >> resolv.new
echo 'search .local' >> resolv.new
mv -f resolv.conf resolv.old
mv -f resolv.new resolv.conf
exit 0
```

Obviously this needs to run with root privileges either by placing a symlink to the script in /etc/cron.daily, or by creating an entry in root's crontab (/var/spool/cron/root), or by creating an entry in /etc/crontab.

---

