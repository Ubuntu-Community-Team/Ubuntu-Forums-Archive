---
title: "Routing problem in ubuntu"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by bamwamba on 2011-03-22
Hello Everyone,

I have installed Ubuntu 10.04 which has an application running on it. Ideally clients would access the application via the ip of this machine. The machine has a static ip address of 10.236.6.131 subnet mask of 255.255.255.0 and gateway of 10.236.6.1. All the pc's on the subnet where the ubuntu machine is are able to access the application running on it by typing the ip of the ubuntu machine in the browser. I can even ping the other machines that are on the same subnet. The problem however comes when the other pc's belonging to different subnets e.g 10.236.5.0, 10.236.7.0, 10.236.8.0 try to access the application running on the ubuntu machine. The machines can't have access and neither can they ping the ubuntu machine.

How do I make the other pc's on the other subnets be able to access the Ubuntu machine?

Thank you in advance for your time and help in resolving this problem am experiencing.

Kind Regards,

---

### Post by deconstrained on 2011-03-22
Set up a bridge, or modify the NAT table of the router.

---

### Post by bamwamba on 2011-03-22
Thank you deconstrained for your prompt response. I forgot to mention that the other machines are able to ping each other regardless of the subnet to which they belong. They are mostly running on windows platform. It's only the Ubuntu machine which cannot be pinged or which can't ping other machines.

Kind Regards,

---

### Post by deconstrained on 2011-03-22
So any other host in the 10.236.6.0 subnet would be pingable by any host in 10.236.7.0, and any host on 10.236.6.0 can ping 10.236.6.131, but no host on 10.236.7.0 can ping 10.236.6.131? That doesn't make much sense. How are these subnets connected in the first place?

Edit: it could be that the routing information supplied to hosts on the other subnets just has the wrong mask, which (and I may be wrong) would exclude host IP's that don't conform to it.

---

### Post by bamwamba on 2011-03-22
Hi deconstrained, thats exactly the scenario. Unfortunately I do not administer this network. I only installed the application on the ubuntu machine which was suppose to be accessed via it's ip. I can engage the network administrator to establish the root cause of this I just thought that maybe there was something I didn't do right on the ubuntu machine which is making it behave this way.

---

### Post by deconstrained on 2011-03-22
If you're not the one in control of the hubs and routers and switches (etc) then there's no telling what it might be; only the sys admin can do anything about it. But ipv4 is ipv4 is ipv4; the platform matters not. So it must be a routing issue.

Edit: assuming, of course, you've ruled out improper firewall and /etc/hosts.allow configuration. Is it set up to allow incoming connections from the other subnets? (Actually that wouldn't stop pings per se unless the firewall was specifically set up to block icmp requests, but it would stop all other requests)

---

### Post by bamwamba on 2011-03-22
> **deconstrained said:**
> Edit: assuming, of course, you've ruled out improper firewall and /etc/hosts.allow configuration. Is it set up to allow incoming connections from the other subnets? (Actually that wouldn't stop pings per se unless the firewall was specifically set up to block icmp requests, but it would stop all other requests)

my /etc/hosts file only has the following entries:

127.0.0.1 localhost
127.0.1.1 savannacom

and then the part for ip6

is this sufficient?

Kind Regards,

---

### Post by deconstrained on 2011-03-22
Take a look at /etc/hosts.deny and /etc/hosts.allow. The content of those files dictates which network hosts are permitted to access the machine, and which are not; see "man hosts_access" for details.

Furthermore, a firewall running locally on the host would block incoming service requests (is there one running?), so making sure the appropriate ports are open might help. Even though it wouldn't stop pings, it would stop other machines from connecting and using the application.

Again, you're certain that 10.236.6.131 is blocking icmp requests from the other subnets but not its own? I highly doubt that would be a firewall issue; you'd have to deliberately configure that sort of specific firewall behavior, which I assume hasn't been done. That's what has me thinking it's a routing issue. If the packets get dropped or returned with a host-unreach message from the broadcast or gateway IP then it's a routing/NAT issue (or at least nothing wrong with the Ubuntu host itself) beyond any shadow of doubt.

---

### Post by bamwamba on 2011-03-22
Thanks deconstrained, let me check the two files then I will revert back soon.

---

### Post by bamwamba on 2011-03-22
I have checked on the two files they do not have anything defined in them. Will /etc/sysctl.conf be another file of interest?

---

### Post by SeijiSensei on 2011-03-22
Try installing traceroute on the server, then use it to see the route to a machine in the 10.236.7.0/24 subnet whose IP address you know.  If the packets make it to the upstream router and die there, the problem is likely misconfiguration of the router.  Perhaps there are rules on the router of which you're unaware.  Regardless, it sounds to me like you need to enlist the network administrator's help in resolving this.

---

### Post by deconstrained on 2011-03-22
> **bamwamba said:**
> Will /etc/sysctl.conf be another file of interest?
Well, yes (very astute observation), but I can't think of any way that stack behavior as specified in that file could result in pings accepted from one subnet and dropped from another. You can control the persistent behavior of the network stack from that file, including how the kernel handles ping requests; the following line, for example, would drop all pings;
net.ipv4.icmp_echo_ignore_all = 1

I would say at this point that, if you've installed Ubuntu on this host and never touched its configuration, it's more likely a problem with the network not routing packets properly than a problem with how Linux is set up.

---

