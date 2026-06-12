---
title: "Intermittent dns failure"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by Don Barnett on 2012-10-29
I have a private network 192.168.3 with Ubuntu server 12.04 running dnsmasq for the dns server (dhcp is disabled).  **Intermittently **one of the work stations on the network will make a call to a page on the local server  and get back a responce "server not found".  The work station may be an xp system or a win 7 system.  The responce is the same on either.  The only resolution we have be able to find is to reboot the windows system that had the error.   This of course is not an acceptable solution.  Do you have any ideas where I should be looking?  My warehouse staff is getting pretty frustrated.

Thanks.

The /etc/network/interfaces file looks like this:
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.3.155
netmask 255.255.255.0
gateway 192.168.3.1
dns-nameservers 192.168.3.155 68.87.69.146
dns-search  farmhome.local [www.farmhome.local](www.farmhome.local)
broadcast 192.168.2.255

The /etc/resolve.conf looks like this:
search farmhome.local
search [www.farmhome.local](www.farmhome.local)
nameserver 192.168.3.155
nameserver 68.87.69.146

---

### Post by Doug S on 2012-10-31
I was hoping someone else would respond, because I am not that confident in what I have to say...
 
Are you sure it is a DNS issue? From your description, it is not clear to me that some network issue or something else might be contributing.
 
Suggest to change this:```
dns-search farmhome.local www.farmhome.local

```to this:```
dns-search farmhome.local

```and this:```
dns-nameservers 192.168.3.155 68.87.69.146
```to this:```
dns-nameservers 192.168.3.155
```Do your windows computers get their network stuff via DHCP? and from where? (you mentioned not from your dnsmasq on your server) When you have the problem, perhaps look at the output from (on the windows computer):```
ipconfig /all
```and compare with when it is working properly.

---

### Post by Don Barnett on 2012-11-21
We discovered that if we wait for about an hour after we get the "server not found" message without rebooting our windows system that the server will mysteriously be found again and everything runs as if no problem occurred.
BTW the broadcast message in my original message has a typo. It is actually 192.168.3.255.  Is that correct?  If you have any ideas I could certainly use the help.

Thanks

---

