---
title: "Erratic ssh connections in Precise"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by feffer on 2012-07-11
Since installing (fresh install from iso) Ubuntu 12.04 LTS, I've had erratic ssh connections. From the 12.04 client machine I can sometimes log into my debian backup server, and other times I get a "Connection refused" error. I've been using openssh for several years and this hasn't happened before. With ssh, it always works when the setup is correct, and always fails if not. None of this, "it worked 10 minutes ago" stuff!

A few days ago, I also installed Kubuntu 12.04 on another partition and have the same problem there. I think this may have something to do with the new network handling in Precise. Namely, the new automatic /etc/resolv.conf and hooks to Network Manager. 

Can anyone confirm erratic ssh behavior on Precise? If so, how did you work around it?

I'm thinking of doing 2 things: 1. remove Network-Manager and configure my wired only machine with /etc/network/interfaces entries. 

2. Comment out the line #dns=dnsmasq in /etc/NetworkManager/NetworkManager.conf

Reading the Ubuntu 12.04 Release notes, I ran across some info about setting up a [static IP in Precise]("http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/"). The author says to use the entries: 
> Q: I use static IP configuration, where should I put my DNS configuration?
A: The DNS configuration for a static interface should go as “dns-nameservers”, “dns-search” and “dns-domain” entries added to the interface in /etc/network/interfacesHowever, he does not show an example, and I haven't been able to find one online. How would I do this?

thx,
feffer

---

### Post by Kirk Schnable on 2012-07-11
I'm running 12.04 on three of my virtual servers on my dedicated box at OVH.  I'm also running it on my desktop at home.  I haven't seen anything like what you're describing... 

Are you sure there's not something erratic about your network connection?  Maybe look at tcpdump or wireshark, and see if the SSH request is even being received by your SSH server. (or being sent by your client for that matter).

That'd probably be a decent starting point in troubleshooting your issue.  

Also, when your SSH server cannot be reached by your 12.04 client, try a client on another computer... might help narrow down where the problem is.

Kirk

---

### Post by feffer on 2012-07-15
Resolved this a few days ago by commenting out the line #dns=dnsmasq in /etc/NetworkManager/NetworkManager.conf

I use the dns resolver on my router (Tomato firmware) to resolve my local network. Ubuntu/Kubuntu 12.04 sets up a localhost resolver. This was conflicting with my router-based resolver. Since making the change, ssh logins to my server work properly.

---

