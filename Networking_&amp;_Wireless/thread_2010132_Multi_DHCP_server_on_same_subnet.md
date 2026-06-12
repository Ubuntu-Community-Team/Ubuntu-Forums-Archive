---
title: "Multi DHCP server on same subnet"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by rockballad on 2012-06-25
Hello,

I need to setup 2 or more DHCP server on the current network. Normally it would cause conflict. Could you please guide me to use iptables or ebtables or anything else to make a DHCP server broadcast to a specific range, or doesn't conflict with another DHCP server?

Many thanks in advance...
Best regards,

---

### Post by SeijiSensei on 2012-06-25
You do realize how DHCP works, right?  The client machines make a broadcast to the all-ones address (255.255.255.255) and wait for a server to respond.  If there are two servers, you'll inevitably have conflicts.  

Why do you "need" two servers?  Are we talking about having a spare in case the other fails?  Then configure a backup server identically to the primary but only bring its dhcpd server online if the other one falls over.  You can automate this with a simple script on the backup that pings the primary every so often and starts its DHCP server if the other isn't visible.  You'll need some bells-and-whistles like having the backup disable dhcpd when the primary server machine comes back online.

If you have some other more unique problem, you'll need to spell it out a bit more.  Almost any solution with multiple servers is probably going to require dividing your network into separate subnets with inter-connecting routers.

---

### Post by rockballad on 2012-06-25
Hello SeijiSensei,

Thanks for your reply. I need 2 DHCP servers because I need to control the way a DHCP server assigns IP to my virtual machines (VM).
I have a default DHCP server, which I can't have access. 
So I need to setup a new DHCP server on my computer, on which I include hard-coded IP (fixed IP) to dhcpd.conf file, these IPs will be assigned to my VM. In another word, I can control this DHCP server.
So I need to add some rules, to make all my VMs only broadcast request to the second DHCP server.

I think about splitting to many subnets but I'd like to ask if I can solve multi DHCP issue first.

Thank you again.

---

### Post by SeijiSensei on 2012-06-25
Why don't you just assign static IPs on the VMs and forget about DHCP entirely? No matter what approach you take, if the VMs are visible to the full network, say via bridging, then you'll have to coordinate with the administrator of the main DHCP server to reserve IP addresses for your VMs anyway.  Just assign the reserved addresses statically.

---

### Post by rockballad on 2012-06-25
I see, However, because the number of VMs are unknown in advance, so static addresses are not suitable.

---

### Post by SeijiSensei on 2012-06-25
In order for a DHCP server to reserve a block of IP addresses, it needs to know the hardware MAC address on each machine. 

Let's take another approach.  Have the VMs operate in their own private network with one bridged VM as the router between the virtual network and the broader network.  Have the router VM run its own copy of DHCP that the other VMs use to get their addresses.  The router VM will also need a couple of iptables 
"NAT" rules to let the other VMs see the broader network, but only the router VM would be bridged and need an external IP address from the main DHCP server. 
 
Now if machines on the physical network need to see individual VMs directly, that makes things tougher.  You need to write iptables rules to forward ports back to the VMs.  If you have to route traffic to specific virtual host:port pairs, things get tricky, but not insurmountable.  I'm hoping the application you have in mind can be supported with a virtual network of VMs with a single virtual router/DHCP server.

I notice that VirtualBox has some features in its "[host-only]("https://www.virtualbox.org/manual/ch06.html#network_internal")" networking mode that might be useful.  It actually includes its own DHCP server which can assign the addresses to the various VM guests.

---

### Post by rockballad on 2012-06-26
Thank you a lot, SeijiSensei. I got your idea. I'll try to write these rules. It's ashamed but I really find it difficult. I'm also afraid that I can make wrong thing to prevent network from working because of bad rules and I can't take it back (remove rules). If you can help me to write some rules and restore-rules (in case I have to remove the rules), it's great. Otherwise, I still thank you so much for giving me a starting point.

---

### Post by SeijiSensei on 2012-06-27
My advice would be to start simple with two VMs in the same virtual network. Get them to where they can see each other.  Then work on getting one of them to see the external network.  When you've accomplished that, it can become the default router for the other machine.  Do a bit of searching for how to build a NAT router.

It does sound like you're taking on a rather complex project without a lot of background in networking.  Maybe you can find a knowledgeable advisor.

Oh, and if you're working entirely with virtual machines, there isn't much you can do to break things.  For starters, you could take the VM host off the external network so it can't interfere with anything else.  All the action at the beginning will be getting the VMs up and running among themselves.  Worst case if you screw something up, you can just blow away the VM and start again.  If I were you, I'd install once instance of the OS then make an immediate snapshot of the clean instance.  If something goes wrong, you have this backup snapshot to reload.

---

### Post by rockballad on 2012-06-27
Thank you again, Sensei! I'll try and report thing later...

---

