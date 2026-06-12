---
title: "VMWARE Ubuntu Bridge not working"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by nanda_justgames on 2009-01-28
Hello fellows....
I have an Ubuntu installed on VMWARE SERVER 2
My objective is to be able to acess my virtual remotely from another site.

But for now I would like only to see my Ubuntu in my windows network.
I've been reading that for me be able to do that, I need to configure my ubuntu to accept bridge connections.

I set up the bridge mode on VMWARE.
But the internet doesn't workd with it (but works fine in NAT).

What Am I missing? 
PS: I'm noob with this bridge  stuff

---

### Post by veloce on 2009-02-10
> **nanda_justgames said:**
> Hello fellows....
I have an Ubuntu installed on VMWARE SERVER 2
My objective is to be able to acess my virtual remotely from another site.

But for now I would like only to see my Ubuntu in my windows network.
I've been reading that for me be able to do that, I need to configure my ubuntu to accept bridge connections.

I set up the bridge mode on VMWARE.
But the internet doesn't workd with it (but works fine in NAT).

What Am I missing? 
PS: I'm noob with this bridge  stuff

If you have correctly set up bridged networking in vmware then your ubuntu vm should have an IP address in the same range as your "windows" network. (Does it?  -open a terminal and type "ifconfig")

If you can ping that ip address from your host computer then the communication is fine.  It could be that the firewall on the windows network prevents access to the internet from your vm - depends on how it is configured.

---

