---
title: "connect to server on a different subnet"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by philipballew on 2011-01-28
i need to set up a ssh and vnc server. the only problem is my client and server are on two different subnets on the same network. how can i still connect?

---

### Post by sikander3786 on 2011-01-28
I think you can turn on IP forwarding on your server and set your server as a gateway for your client PCs. Make sure any firewalls on the network allow traffic exchange for your SSH port.

---

### Post by philipballew on 2011-01-31
alright. well then what exactly is this and how do i connect to it from my laptop?

---

### Post by YesWeCan on 2011-01-31
Hmm. Of course the purpose of having different subnets is to prevent devices on one subnet from being able to communicate with those on the other. I do not believe a single NIC will support multiple subnets. Typically, communication between subnets requires a router.

So I suspect your only option, without using a router, is to configure both client and server to use the same subnet. Add a NIC to the server or manually reconfigure your laptop to use the servers subnet when you want to do remote desktop.

---

### Post by Iowan on 2011-01-31
I'm kinda rusty - but it WAS possible to alias an interface.  [This]("http://manpages.ubuntu.com/manpages/hardy/man8/ifconfig.8.html") is a dated manual - >        interface
              The name of the  interface.   This  is  usually  a  driver  name
              followed  by  a  unit  number,  for  example  eth0 for the first
              Ethernet interface. If your kernel  supports  alias  interfaces,
              you  can  specify  them with eth0:0 for the first alias of eth0.
              You can use them to assign a second address. To delete an  alias
              interface use ifconfig eth0:0 down.  Note: for every scope (i.e.
              same net  with  address/netmask  combination)  all  aliases  are
              deleted, if you delete the first (primary).
You'd still need to figure out forwarding, though...

---

### Post by philipballew on 2011-02-01
anyone know a definitive answer on the original question?

---

### Post by mips on 2011-02-01
> **philipballew said:**
> i need to set up a ssh and vnc server. the only problem is my client and server are on two different subnets on the same network. how can i still connect?

Got a simple diagram?

---

### Post by YesWeCan on 2011-02-01
> **Iowan said:**
> I'm kinda rusty - but it WAS possible to alias an interface.  [This]("http://manpages.ubuntu.com/manpages/hardy/man8/ifconfig.8.html") is a dated manual - You'd still need to figure out forwarding, though...

This occurred to me as well but I can't find any answer on whether the alias can be on a different subnet. I know a NIC can support two IP addresses on the same subnet.
This how-to says they have to be on the same subnet.
[http://www.cyberciti.biz/faq/linux-creating-or-adding-new-network-alias-to-a-network-card-nic/](http://www.cyberciti.biz/faq/linux-creating-or-adding-new-network-alias-to-a-network-card-nic/)

---

### Post by YesWeCan on 2011-02-01
> **philipballew said:**
> anyone know a definitive answer on the original question?

Options have been suggested. What are your constraints?

You can change your laptops subnet
You can add a NIC to the server
You can even use a router. This might be a very good solution if you have one handy.
You could add another NIC to your laptop, perhaps there is a USB device available.

:)

---

### Post by philipballew on 2011-02-01
well its not my network because i live at a university

---

### Post by philipballew on 2011-03-25
bump

---

### Post by SeijiSensei on 2011-03-25
> **philipballew said:**
> i need to set up a ssh and vnc server. the only problem is my client and server are on two different subnets on the same network. how can i still connect?

Every day we all communicate with machines on different subnets across the globe so it's obviously possible to do so.

You just haven't given us enough information about the network architecture.  Can you ping the server from your client?  How about running a traceroute?  Does the trace die at some intermediate router? Perhaps there's some firewalling between the subnets?  Have you asked your university's IT people how to solve this problem?  Maybe their policies don't permit what you're trying to do.

---

