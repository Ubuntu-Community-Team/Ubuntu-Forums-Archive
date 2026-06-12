---
title: "DNS resolves but can't ping internet"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by izziere on 2009-06-05
After multiple problems which started when I moved, I am having difficulty with internet connection.  I can successfully ping the router and other hosts on the LAN but only by using IP address.

My /etc/hosts file is set up correctly, as is my interfaces file and my resolv.conf file (pointing to router).  I cannot post here as I have no internet connection on that computer!

If I ping, say, [www.google.com](www.google.com), it identifies the IP as 209.85.229.103 but all packages are lost.  The same happens if i ping that IP address.  If I use traceroute, it gets lost after connecting to my router/gateway.

host [www.google.com](www.google.com) gives me the IP addresses.

I have tried with both DHCP and static IPs.

I am at my wit's end - can anyone help, please?

Router is D-Link DSL-2740B.

Thanks!

---

### Post by grumbl on 2009-06-05
Maybe a silly question, but have you set your default gateway, and if so, is it your router ( which i suspect is correct and set for the other hosts in your network ) ?

---

### Post by Brandon Williams on 2009-06-05
ping and traceroute are not reliable ways to test connectivity. It is quite common for routers and firewalls to be configured to ignore unsolicited ICMP. traceroute is a little bit better, but will still have limited end-to-end utility because a lot of routers and firewalls will also be configured in a way that disrupts traceroute.

On my system, where internet connectivity is working just fine, I can't ping or traceroute to [www.google.com](www.google.com) either, regardless of whether I specify the hostname or the IP address. The symptoms are exactly as you describe.

However, I _can_ trace the route using tcptraceroute (sudo aptitude install tcptraceroute; tcptraceroute [www.google.com](www.google.com) 80;). I suggest that you switch to this tool for your testing if possible. I understand that you might not be able to install it due to the fact that you don't have internet connectivity, but at least try to connect using telnet to port 80 (telnet [www.google.com](www.google.com) 80). If that works, telnet will output 'Connected to [www.google.com](www.google.com)' or something similar, and you will know that the problem is firefox, not your internet connection.

If it still doesn't work after this, I suggest that you log in to your internet gateway and use that tools that are (hopefully) built into the unit to attempt to test external connectivity.

---

### Post by izziere on 2009-06-07
Nice tips, thanks.

Yes I can get a tcptraceroute through to google, etc.  No internet connection though.  As it is a server I use lynx.  It hangs on the message initiating http connection.

It may be connected or it may not be, but reconciling the server name and IP has a couple of other connotations:

* Port forwarding on the routers (I have tried two now) does not forward http requests on port 80 to the server, it brings up the router web front end (not ideal!)
* Accessing server files via samba is not possible from my XP device when using path \\ServerName\shared_file_directory, only using \\192.168.1.nnn\shared_file_directory.
* likewise I can SSH into the machine using its IP address but not its servername.

However, these may not be connected and I am keen to get internet connection up and running first so that I don't have to keep downloading packages on another machine and swapping across.

My /etc/hosts file is unchanged and worked before, so I am at a loss...

---

### Post by Brandon Williams on 2009-06-07
Try running tcpdump in one terminal will attempting to connect in a different terminal. For tcpdump, just dump everything: 'tcpdump -i any -vvv'. You may want to dump the output to a file to make sure that you don't miss anything important.

For the tests, first connect to [www.google.com](www.google.com) with telnet, since this should work. Then, attempt to connect to [www.google.com](www.google.com) using lynx. Compare the output from the successful and the unsuccessful connections in order to determine what is different about the two.

---

### Post by superprash2003 on 2009-06-08
you could try changing MTU values since your pings are unsuccessful [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

