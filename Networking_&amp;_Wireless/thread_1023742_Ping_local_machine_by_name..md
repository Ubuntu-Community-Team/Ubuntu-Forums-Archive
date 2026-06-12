---
title: "Ping local machine by name."
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by bqm3043 on 2008-12-28
I can access the Internet fine, and ping by Internet sites by name. But, can't ping local machines by name...

ping computer_name
result is "ping: unknown host computer_name"

I can ping local computers by ip address.

What do I need to change for the local network to be able tu use names instead of only ip address's?

---

### Post by atoponce on 2008-12-28
How do you have name resolution setup? The way DNS works is when resolving non-fully qualified domain names, you append the argument to 'search' or 'domain' in your /etc/resolv.conf file. That is usually written from your DHCP server.

To give you an idea, say you own the 'example.com' domain. Tell your DHCP server that the domain you're a member of is example.com. Then, when you receive a DHCP lease, your /etc/resolv.conf will be overwritten, specifying the 'search' or 'domain' line as example.com. Also, it will append 1, 2 or 3 'nameserver' lines that are responsible for resolving DNS requests (also part of the DHCP lease). If you have a DNS server on your network, and you've told the DHCP server about it, then the DNS server will need to have an entry in the zone file for all the machines in your 'example.com' domain.

For example. say you have the boxes 'server', 'work1' and 'work2' as hostnames. Edit your example.com zone file, put those entries in there, pointing to their appropriate IP addresses. Restart your DNS server, then pinging 'server' will work, because it will take the 'example.com' argument from the 'search' line in your /etc/resolv.conf, and ping 'server.example.com'. This will be found in the DNS zone file, return the IP, which will ping the appropriate IP address.

That's a brief rundown of how DNS works with DHCP. If you don't want to setup a DHCP and DNS server (I don't blame you), then you can put the hosts in your /etc/hosts file as a shortcut:

```
192.168.0.1    server
192.168.0.2    work1
192.168.0.3    work2
```

At least now, you have a basic understanding of what is going on when you try to 'ping work1', and it's not working.

---

### Post by bqm3043 on 2008-12-28
Thanks for the quick reply. So if I understand correctly, I need to add the other local computer, xray to the hosts file. The hosts file after the change is listed below. 

127.0.0.1	localhost
127.0.1.1	hp-desktop
192.168.7.17    xray

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Thanks again for your help.

---

### Post by AlanR8 on 2008-12-28
adding machine names to the hosts file is fine and works well. However, if your router dishes out IP addresses dynamically, the computer addresses can change. That's been my experience so I found another way in these forums, thanks to the original poster:

> edit /etc/nsswitch.conf

Rem (#) the line that says
Quote:
hosts: xxxxxxxxxxxxxxx

to this:
Quote:
hosts: files dns wins 

finally, you need to install winbind
Code:
sudo apt-get install winbind
that's all that it took for me.

now ping <hostname> works great. And I can finally use the built-in terminal server client with hostnames instead of IP addresses.

---

### Post by bqm3043 on 2008-12-28
It worked! I already had winbind in Ubuntu 8.10. I changed hosts line in /etc/nsswitch.conf, and rebooted. What is the other items in the hosts line for?

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

#hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

Thanks again for your help.

---

### Post by AlanR8 on 2008-12-28
You're welcome

---

### Post by iconoclast hero on 2011-05-23
This worked great for 3/4s of my computers, but when I tried to ping this machine by name from another computer, unknown host was returned.  (When pinging from local host, it works.)  When I looked at the router table, the other computers have something listed under "attached devices" except this one...while I using only wlan0 with a fixed ip address.  

I thought about it and grabbed my ethernet cable and plugged it into my machine (eth0 is DHCP).  I checked the router table and now it shows wlan0 with the proper computer name properly, but it doesn't have anything under eth0...and of course when I unplug eth0, the device name under wlan0 disappears again.

Is there anyway to fix this?  Since I generally use this computer, it isn't a big deal, I'm just wondering.  I'm running DHCP from a Netgear WNR834Bv2.

---

