---
title: "VPN question: can't connect under 13.04, can connect under 12.04"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by mawxcarroll on 2013-05-17
Hi,
  First, quick background:  On my old 12.04 laptop I routinely used netExtender to connect to my college's VPN.  I got a new laptop and installed 13.04 and now I cannot connect.

I then installed 12.04 on the new laptop so that I could compare a fresh install in both cases.  Under the new install of 12.04, netExtender connects and works fine.  Under the new install of 13.04, netExtender gives an error:

Error determining existing route to SSL VPN

Seems like this should be fixable since it works great in 12.04!  Anyone have any suggestions?  Here's the logfile with the errors (note that under 12.04 all of the DNS messages are not there):

```
05/17/2013 11:52:14.829 [general warn     2485] Error determining existing route to SSL VPN
05/17/2013 11:52:14.841 [general notice   2485] SSL Connection is ready
05/17/2013 11:52:15.843 [general info     2485] Using new PPP frame encoding mechanism
05/17/2013 11:52:15.844 [general info     2485] Using PPP async mode (chosen by server) 
05/17/2013 11:52:15.844 [general info     2485] Connecting tunnel...
05/17/2013 11:52:19.037 [connect info     2610] NetExtender interface up
05/17/2013 11:52:20.037 [dns     notice   2610] Setting up DNS
05/17/2013 11:52:20.044 [general info     2610] Setting up DNS suffixes
05/17/2013 11:52:20.100 [general info     2620] Monitoring processes:  nx=2485, pppd=2555
05/17/2013 11:52:20.100 [dns     info     2620] Monitoring nameserver: 198.17.40.11
05/17/2013 11:52:20.100 [dns     info     2620] Monitoring nameserver: 198.17.40.113
05/17/2013 11:52:20.100 [dns     info     2620] Monitoring DNS suffix: ursinus.local
05/17/2013 11:52:20.100 [dns     info     2620] Monitoring DNS suffix: ursinus.edu
05/17/2013 11:52:24.101 [dns     warn     2620] DNS suffix "ursinus.local" is no longer configured locally
05/17/2013 11:52:24.102 [dns     warn     2620] DNS suffix "ursinus.edu" is no longer configured locally
05/17/2013 11:52:24.104 [general info     2622] NetExtender DNS helper launched
05/17/2013 11:52:24.105 [dns     notice   2622] Restoring DNS settings
05/17/2013 11:52:24.105 [dns     notice   2622] Setting up DNS
05/17/2013 11:52:24.116 [general info     2622] Setting up DNS suffixes
05/17/2013 11:52:29.120 [dns     warn     2620] DNS suffix "ursinus.local" is no longer configured locally
05/17/2013 11:52:29.120 [dns     warn     2620] DNS suffix "ursinus.edu" is no longer configured locally
05/17/2013 11:52:29.123 [general info     2631] NetExtender DNS helper launched
05/17/2013 11:52:29.123 [dns     notice   2631] Restoring DNS settings
05/17/2013 11:52:29.123 [dns     notice   2631] Setting up DNS
05/17/2013 11:52:29.133 [general info     2631] Setting up DNS suffixes
05/17/2013 11:52:34.137 [dns     warn     2620] DNS suffix "ursinus.local" is no longer configured locally
05/17/2013 11:52:34.137 [dns     warn     2620] DNS suffix "ursinus.edu" is no longer configured locally
05/17/2013 11:52:34.140 [general info     2640] NetExtender DNS helper launched
05/17/2013 11:52:34.140 [dns     notice   2640] Restoring DNS settings
05/17/2013 11:52:34.141 [dns     notice   2640] Setting up DNS
05/17/2013 11:52:34.146 [general info     2640] Setting up DNS suffixes
05/17/2013 11:52:34.150 [dns     warn     2620] Fixed DNS settings 3 times in a row; giving up for 1 minute
05/17/2013 11:53:34.163 [dns     info     2620] Resuming DNS monitoring
05/17/2013 11:53:34.164 [dns     warn     2620] DNS suffix "ursinus.local" is no longer configured locally
05/17/2013 11:53:34.164 [dns     warn     2620] DNS suffix "ursinus.edu" is no longer configured locally
05/17/2013 11:53:34.166 [general info     2692] NetExtender DNS helper launched
05/17/2013 11:53:34.167 [dns     notice   2692] Restoring DNS settings
05/17/2013 11:53:34.167 [dns     notice   2692] Setting up DNS
05/17/2013 11:53:34.173 [general info     2692] Setting up DNS suffixes
05/17/2013 11:53:34.176 [dns     warn     2620] Fixed DNS settings 4 times in a row; giving up for 1 minute
```

---

### Post by mawxcarroll on 2013-05-19
I figured out a work around for my issue.  By comparing diagnostic output from the working netExtender in 12.04 to the non-working netExtender in 13.04, I was able to determine that the ip address of the vpn was not being added to the routing table.  What's strange is that routing information for all of the intranet *was* being added to the routing table -- there was just no way to get to it since the vpn itself wasn't there.

My workaround is just to manually add the vpn to the routing table with

```
sudo route add -net <vpn ip address> netmask <netmask for your vpn> gw <gateway for your vpn> dev <your device, eth1 in my case>
```

If you ping your vpn hostname, you can quickly find the ip address.  I actually don't know how to find the other information in general -- I obtained it from the diagnostic output of the working copy of netExtender.

I've just created a simple script that adds the necessary route to the table every time I connect with netExtender.  Not sure why netExtender is not doing this correctly under 13.04!

Hopefully this helps someone!

Cheers,
tom

---

