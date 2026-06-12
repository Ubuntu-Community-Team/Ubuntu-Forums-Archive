---
title: "Server with 2 IP addresses - only 1 is pingable"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by oboyledk on 2011-04-04
I'll try to explain my issue and then include my interfaces file below,
 
I have a server with 2 separate physical NIC cards and 2 separate IP addresses.  One card, running 10.10.5.48 is pingable on all subnets.  The other card, with an IP of 10.10.88.2 is only reachable from an IP on the same subnet as 88.2.  If I disable the 10.10.5.48 card, the 88.2 IP is accessable over all subnets.  
 
I think this is a routing issue, but I'm not sure how to fix it.  Our network Admin has assured me that the issue is within the server, and not across the network.  **It's really important for what I'm doing that both IP's be available across all networks** - the 88 subnet acts as a separate tftboot Vlan using FOG for imaging systems over our network.  The 5.48 subnet is a management IP and should be accessable even when 88 is busy.  
 
Pictures below, any help is appricaited!:popcorn:
 
My interfaces File
[IMG]http://dl.dropbox.com/u/3761224/ubuntu%20help/interfaces.PNG[/IMG]
 
My routing list
[IMG]http://dl.dropbox.com/u/3761224/ubuntu%20help/netstat.PNG[/IMG]
 
And from another view..
[IMG]http://dl.dropbox.com/u/3761224/ubuntu%20help/routing1.PNG[/IMG]

---

