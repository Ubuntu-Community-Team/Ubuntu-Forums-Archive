---
title: "Prefer wireless over wired"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by njparton on 2010-06-01
ubuntu automatically prefers wired connections over wireless.
 
I have a similar set up to you and I'm desperately trying to find a way to set my wireless connection as a high priority.  My wired connection also goes to a switch and then a NAS so no internet connection down that branch.
 
The wired branch of my network all have 192.168.2.x address and the wireless 192.168.1.x.  So basically I either need to set the wireless as higher priority or use iptables (aaargh) to stop internet packets going down the 192.168.2.x branch.
 
Can anyone help us out? I currently have to disable eth0 to get onto the internet...

---

### Post by BoneKracker on 2010-06-01
> **njparton said:**
> ubuntu automatically prefers wired connections over wireless.
 
I have a similar set up to you and I'm desperately trying to find a way to set my wireless connection as a high priority.  My wired connection also goes to a switch and then a NAS so no internet connection down that branch.
 
The wired branch of my network all have 192.168.2.x address and the wireless 192.168.1.x.  So basically I either need to set the wireless as higher priority or use iptables (aaargh) to stop internet packets going down the 192.168.2.x branch.
 
Can anyone help us out? I currently have to disable eth0 to get onto the internet...
Hint: Ever notice when you run 'ifconfig' it has a field labeled "Metric"?

---

### Post by njparton on 2010-06-01
Yes, and I realise that it can also be set in the interfaces file, but I was worried that with the new network manager that this file wasn't used any longer?

---

### Post by BoneKracker on 2010-06-01
> **njparton said:**
> Yes, and I realise that it can also be set in the interfaces file, but I was worried that with the new network manager that this file wasn't used any longer?

I don't use Ubuntu and I use my own routing scripts, so I don't know.  But a quick Google turned this up, which may be applicable (It's from the 8.04 release notes, at which time the default routing metric and metric handling changed).
[http://www.ubuntulinux.org/getubuntu/releasenotes/804](http://www.ubuntulinux.org/getubuntu/releasenotes/804)

I take it to mean you can still manage it in your interfaces file; a default metric of 100 is applied if nothing is set there.
> Route metrics

ifupdown now sets the default route metric to 100 for interfaces with no metric option set in /etc/network/interfaces. This change makes no difference for most users, but may affect a few users with complex networking requirements. If you rely on the previous default route metric of 0 (zero), edit /etc/network/interfaces and set the metric option explicitly for your interface, for example:

      	iface eth0 inet static
      	address 192.168.0.2
      	network 192.168.0.0
      	broadcast 192.168.0.255
      	netmask 255.255.255.0
      	gateway 192.168.0.1
      	metric 0

Network Manager

In Ubuntu 8.04, network-manager only manages interfaces that are marked for roaming. Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade. Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces. If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network

---

### Post by njparton on 2010-06-01
my interfaces file doesn't contain a eth0 or wlan0 entry so I think it's redundant now???

---

### Post by chewearn on 2010-12-11
I got to this thread from searching on how to prefer wireless connection over wired in Ubuntu, while still having both connection enabled.  Unfortunately, the discussion ended without a solution, so I started poking around.

In my particular set-up, my notebook connects to the Internet via wireless broadband.  However, I sometimes also connect the wired eth to my local network to access local resources.  By default when I did that, Ubuntu now routes all Internet traffic through wired eth, and ignore the wireless broadband connection.

What I wanted instead is for all Internet traffic to continue to be routed via wireless broadband, but any local network traffic finds the wired eth.

The solution is actually quite simple using the Network Manager:

> Right click on Network Manager icon > select "Edit Connections..."
> Under "Wired" tab, click "Add" button.
> Enter something meaningful under "Connection name"; I use "Auto eth local".
> Select IPv4 Settings, choose the appropriate item under "Method".  I use "Automatic (DHCP)" because I do have a router/gateway/DHCP server on my local network.  The wired eth will thus get it's IP from the local DHCP server.
> Click "Routes..." button on the bottom right corner of the dialogbox.
> Enable the checkbox: "Use this connetion only for resources on its network".
> Select "OK" > select "Apply".

Done!

---

### Post by stephanunc on 2013-03-26
Thank you, this works! For anyone who wants to use wireless as a network priority over eth0, this works in Ubuntu 12.10

> **chewearn said:**
> I got to this thread from searching on how to prefer wireless connection over wired in Ubuntu, while still having both connection enabled.  Unfortunately, the discussion ended without a solution, so I started poking around.

In my particular set-up, my notebook connects to the Internet via wireless broadband.  However, I sometimes also connect the wired eth to my local network to access local resources.  By default when I did that, Ubuntu now routes all Internet traffic through wired eth, and ignore the wireless broadband connection.

What I wanted instead is for all Internet traffic to continue to be routed via wireless broadband, but any local network traffic finds the wired eth.

The solution is actually quite simple using the Network Manager:

> Right click on Network Manager icon > select "Edit Connections..."
> Under "Wired" tab, click "Add" button.
> Enter something meaningful under "Connection name"; I use "Auto eth local".
> Select IPv4 Settings, choose the appropriate item under "Method".  I use "Automatic (DHCP)" because I do have a router/gateway/DHCP server on my local network.  The wired eth will thus get it's IP from the local DHCP server.
> Click "Routes..." button on the bottom right corner of the dialogbox.
> Enable the checkbox: "Use this connetion only for resources on its network".
> Select "OK" > select "Apply".

Done!

---

### Post by wildmanne39 on 2013-03-26
Thread closed. Please do not post in old threads.

---

