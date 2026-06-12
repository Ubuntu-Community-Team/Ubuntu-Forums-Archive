---
title: "Network will not route."
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by Mordekai on 2009-06-01
Hi All,

Perhaps I am simply being ignorant here... but I am having an issue that seems simple, but I cannot resolve.

On a new install of Ubuntu server upon a Dell 1850, all went well, except now that everything is installed I cannot manage more than local network access.

The machine was originally set for DHCP, and this resulted in it being able to ping by IP locally, Ping by network name locally, and resolve DNS for any name either internal or on the internet. But so far as connectivity to the "outside" is concerned, nothing.

So I thought firewall - nope no firestarter is installed with the server release.

So I thought gateway, and proceeded to set all the network properties manually, including the DNS settings of course... this resulted in the same situation as the DHCP did (albeit with a static IP of course). Pinging internet servers still results in no response.

The config is pretty standard, my network is on a 192.168.100.x subnet, the router/gateway is at 192.168.100.1. DNS is provided via a DNS server on the same subnet, that gets all internet without issue, as do all other boxes both windows and *nix.

My question is "what am I missing?". Is there something in Ubuntu server that disables this connectivity out of the box?

Thanks for any and all help.

---

### Post by Mordekai on 2009-06-01
I have an update.

It turns out that the ports on the local switch were configured for Link Agregation (or interface bonding) , and once I removed one of the interface cables all routing was well.

Having found this, I set up interface bonding using the guide [here]("http://ubuntuforums.org/showthread.php?t=785471") and rebooted the server for good measure.

Sadly however, this did not fix the issue and the same problem existed as soon as I plugged eth1 back in.

I then apt-get installed the  "ifenslave" package (after already installing the ifenslave-2.6 package) and restarted the networking.
Now from what I have read, this should make no difference, but directly after this the symptoms changed.
Now, ping for internet sites works (but is VERY slow to respond) and ping for the local network is "Unreachable". As before, the DNS queries all work well, and networking is correct and fast if you unplug the eth1 interface.


Ideas?

---

