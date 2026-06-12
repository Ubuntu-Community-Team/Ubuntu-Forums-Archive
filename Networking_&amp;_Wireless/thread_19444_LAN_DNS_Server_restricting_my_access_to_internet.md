---
title: "LAN DNS Server restricting my access to internet"
date: 2005-03-11
forum: Networking &amp; Wireless
---

### Post by Benf on 2005-03-11
This is more of a general network question rather than one specifically for Ubuntu.

I live in a dorm at a college, and each dorm is on its own LAN.  We get our internet through this lan.

I have an Ubuntu box that had been accessing the network fine for months.  It recently stopped being able to access the internet.  Upon checking the cause of the problem, I found that it found a DNS server at 192.160.2.1 and a domain called "Matt."  Does this mean that someone recently, for some reason, set up a DNS server on our lan?  No one else if getting this problem, so I'm assuming it's restricted to linux (everyone here runs windows).  When I boot to windows (it's a dual boot) I get a correct ip.

So would I be correct in assuming some kid is screwing up our lan by running a linux dns server (for some reason) and I'm being assigned a local ip by it?

What are some fixes for this?  It won't allow me to add a dns server and I need it to see the university one.

Thanks for any help,
Benf

---

### Post by alastair on 2005-03-12
For a start, it would be a good idea to note how the network is generally set up i.e. network numbers etc.

In XP, with the network working, one way is to open a DOS shell and type :

ipconfig /all

This might be a DHCP problem rather than DNS - assuming your network is setup to get IP addresses, DNS servers, gateway etc. from a DHCP server. DHCP client /broadcast/ for a DHCP server - and perhaps someone has set up their own unofficial one - which has replid to you and given you wrong information.

See your system logs :

/var/log/syslog

and check if DHCP is the cause. If "dhclient" is your DHCP client, see :

man dhclient
man dhclient.conf

---

### Post by reubadoob on 2007-03-16
I am having the same problem but with a bit of a twist. My school requires that all computers be registered. The only problem is I can't seem to point Ubuntu's firefox to go the net reregistration page. My XP pc goes there just fine and I can verify that is registered. But of course my school does not support Linux/Unix. SO if anyone has ANY suggestion how to get my Ubuntu onto the web please give them. I've tried as much as I could find. 

Here's the link to my schools RESNET if this is any help:

[https://umdrive.memphis.edu/d-reslife/resnet/index.html#]("https://umdrive.memphis.edu/d-reslife/resnet/index.html#")

---

