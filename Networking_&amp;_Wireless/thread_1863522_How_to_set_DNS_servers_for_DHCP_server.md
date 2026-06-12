---
title: "How to set DNS servers for DHCP server?"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by AlexBooton on 2011-10-17
Hi,

I'm confused.  I want all clients on the LAN to use OpenDNS as the DNS server.

Eth1 is the LAN side nic and a DHCP server.

I went to System/Admin/Network Tools/Devices/eth1/Configure/Auto eth1/Edit/IPv4 Settings and set the DNS Servers as "208.67.222.222,208.67.220.220"

As an aside, on that same page, what is the text box labeled "Search Domains"?  What's the difference between DNS Servers and Search Domains?

But the main problem is the DNS servers I specified are not propagated to the clients.  If I let the client automatically obtain DNS Servers, it does NOT get those two DNS servers (it doesn't even get one).  In fact it gets 208.78.99.218 and I don't even know if that's a real DNS server.

I looked in /etc/network/interfaces and the only thing there is:
   auto lo
   iface lo inet loopback

So where are the interface settings for eth0 and eth1?

Any help will be greatly appreciated.

---

### Post by papibe on 2011-10-17
Are you running dhcp3-server?

If so, the DNS given to its clients is set in the file: 
```
/etc/dhcp3/dhcpd.conf
```
You need to modify the line containing the domain-name-servers key, so it looks like this:
```
option domain-name-servers 208.67.222.222, 208.67.220.220;
```
Restart the service on the server, and reboot a client to test the settings.

Is that what you are looking for?
Regards.

---

### Post by AlexBooton on 2011-10-18
Hi papibe,

Thanks for your help!

It turns out I did not have dhcp3-server installed.  I did have isc-dhcp-server and that "seemed" to be working.

Now I've installed dhcp3-server but all I have in /etc/dhcp3 is another subdir: dhclient-enter-hooks.d, and that has one file: samba.

It seems something is not right.  Where do I go now?

Thanks

---

### Post by AlexBooton on 2011-10-18
Hi,

OK, AFAICS, dhcpd is running and I want to get dhcp3d to run instead.

I thought I should uninstall isc-dhcp-srever and install dhcp3-server but the later appears to depend on the former.

I tried:
   service dhcpd restart 
and it said "unrecognized service"

but:
  ps -A | grep dhcp
gives 4966 ?   00:00:00 dhcpd

So 
1: How do I restart the service 
and 
2. How do I kill the old service and start dhcpd3

I'm uneasy about killing the service unless I can start the new service.  This is a running system with users so don't want to reboot and/or kill a service and not be able to restart it.

Thanks

---

### Post by mörgæs on 2011-10-18
Moved to Networking and Wireless.

---

### Post by papibe on 2011-10-18
Kind of my mistake :confused:

I just learned reading the packaged documentation, that apparently from Natty and beyond, dhcp3-server became a transitional package, and the correct one is isc-dhcp-server (actually dhcp3-server is now included on isc).

My guess is that you are running 11.*, so you need to install the package again. Just to be sure :
```
$ sudo apt-get remove dhcp3-server
$ sudo apt-get autoclean
$ sudo apt-get autoremove
$ sudo apt-get update

```
and then:
```
$ sudo apt-get install isc-dhcp-server
```
That package is the one including the file /etc/dhcp3/dhcpd.conf, so after this go ahead and configure you DNS.

Sorry about the confusion, I hope you can solve your problem now.

Tell us how it goes,
Regards.

---

### Post by Hulkiedulkie on 2011-10-18
Just some additions
- conf file can be found in /etc/dhcp/dhcpd.conf since 11.04.
- AFAIK dhcp3 is deprecated because it can not provide different services to different interfaces.
- the service can be restarted, stopped etc with the following command
```
service isc-dhcp-server restart
service isc-dhcp-server stop
```

---

### Post by AlexBooton on 2011-10-19
Thanks to you all for your help!

There was a bit of confusion re: dhcp3.  I now see that the "correct" dhcp server package is isc-dhcp-server.  

It is very confusing.

Thanks for the proper method for setting dhcpd's DNS Servers.

It's very confusing that System/Administration/Network tools offers a way to specify the DNS Servers but doesn't work!

Thanks for the heads up for re-starting and stopping the service via "service isc-dhcp-server restart".  That was a huge help.

All in all, you guys are a great help!

AB

---

### Post by mörgæs on 2011-10-19
If this means that the thread is solved, please mark it so using 'thread tools' :-)

---

### Post by AlexBooton on 2011-10-19
Done.  Thanks for the reminder.

---

