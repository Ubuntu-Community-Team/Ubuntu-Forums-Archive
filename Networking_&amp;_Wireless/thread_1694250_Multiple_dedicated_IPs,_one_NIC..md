---
title: "Multiple dedicated IPs, one NIC."
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by Ericatang on 2011-02-24
Hello, 

I've been doing some research on what the necessary steps would be to have multiple dedicated WAN IPs through one NIC, and how one would go configuring a VM (using VirtualBox), on Ubuntu 10.10 server to use one of said dedicated IPs, but haven't found anything definitive. 

Does anyone know how I could achieve this?

Thanks!

P.S: (I was debating on whether or not this topic should be posted here, or in Ubuntu Server section, but I presume this is more of a networking question than an ubuntu server question).

---

### Post by penseBien2 on 2011-02-24
> **Ericatang said:**
> Hello, 

I've been doing some research on what the necessary steps would be to have multiple dedicated WAN IPs through one NIC, and how one would go configuring a VM (using VirtualBox), on Ubuntu 10.10 server to use one of said dedicated IPs, but haven't found anything definitive. 

Does anyone know how I could achieve this?

Thanks!

P.S: (I was debating on whether or not this topic should be posted here, or in Ubuntu Server section, but I presume this is more of a networking question than an ubuntu server question).

I dont think that is possible if you are to use it on one NIc

---

### Post by dmizer on 2011-02-24
> **Ericatang said:**
> Hello, 

I've been doing some research on what the necessary steps would be to have multiple dedicated WAN IPs through one NIC, and how one would go configuring a VM (using VirtualBox), on Ubuntu 10.10 server to use one of said dedicated IPs, but haven't found anything definitive. 

Does anyone know how I could achieve this?

Thanks!

P.S: (I was debating on whether or not this topic should be posted here, or in Ubuntu Server section, but I presume this is more of a networking question than an ubuntu server question).

Actually, this is a virtualization question, but you'll basically have to manually change the routing tables with the "route" command.

That said, I am not sure if it's possible to have multiple WAN IP addresses on one physical NIC. It is possible to have multiple LAN IP addresses, but since each WAN needs a separate physical connection, I seriously doubt it's possible without another NIC.

It is extremely easy to add a second NIC, and they are quite cheap. If you are in a situation where you are able to use multiple WAN APs, It would be worth your while to invest in another NIC.

---

### Post by SeijiSensei on 2011-02-24
You can create multiple virtual interfaces on any NIC with ifconfig using the "ethN:n" convention:

```
ifconfig eth0:0 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255
```

You can continue with eth0:1, eth0:2, ..., and assign them to different IPs.

I've run public servers with multiple interfaces in a number of situations, particularly when I want to support both HTTP and HTTPS on the same machine.

---

### Post by psusi on 2011-02-24
> **SeijiSensei said:**
> 
I've run public servers with multiple interfaces in a number of situations, particularly when I want to support both HTTP and HTTPS on the same machine.

You don't need a second IP address for that; they use different ports.

---

### Post by Fire_Chief on 2011-02-24
If you're going to be running Virtualbox and using the extra IPs only for those VMs, then the easiest thing to do is configure the networking on the individual VM to use bridged networking instead of NAT (default). This way the guest VM will connect directly to the physical network as if it were another host on the network. No fancy changes required on the Linux host system.
:guitar:

Cheers!

EDIT: This is assuming that all of your additional dedicated IPs are on the same subnet as the host Linux system.

---

### Post by SeijiSensei on 2011-02-24
> **psusi said:**
> You don't need a second IP address for that; they use different ports.

Yes, I know that, but sometimes you need to have multiple SSL servers with separate certificates.  Up until recently you couldn't use name-based virtual hosts for SSL, so being able to assign an extra IP to HTTPS can be very helpful.

[quote=Ericatang]how one would go configuring a VM (using VirtualBox), on Ubuntu 10.10 server to use one of said dedicated IPs[/quote]

Just curious, but why do you need to run a VM?  An individual Linux server can provide a wide array of network services.  I've never had to use a VM on a Linux server, only on the desktop to run Windows under Linux.  I can understand using VM's to host a second OS, but if all the instances are running Linux, isn't it easier just to run all the services on one instance?

As an alternative to bridging, you could use routing and masquerading rules on the host to send traffic between the guest VM"s virtual interface and an associated external one on the host.

---

### Post by Ericatang on 2011-02-25
> **SeijiSensei said:**
> Yes, I know that, but sometimes you need to have multiple SSL servers with separate certificates.  Up until recently you couldn't use name-based virtual hosts for SSL, so being able to assign an extra IP to HTTPS can be very helpful.



Just curious, but why do you need to run a VM?  An individual Linux server can provide a wide array of network services.  I've never had to use a VM on a Linux server, only on the desktop to run Windows under Linux.  I can understand using VM's to host a second OS, but if all the instances are running Linux, isn't it easier just to run all the services on one instance?

As an alternative to bridging, you could use routing and masquerading rules on the host to send traffic between the guest VM"s virtual interface and an associated external one on the host.


Firstly, thanks for all the prompt replies, they're appreciated. As for your question, I'm actually attempting to start a small hosting company, and we're wanting to provide VPS hosting as one of our services, and dedicated IP's seem to be the norm for such things, so I was trying to figure out how one would achieve that (a VM with a dedicated IP) I'm not entirely sure of the setup at the data centre, perhaps I'm misunderstanding and it would be possible to have multiple LAN ips assigned their own dedicated by the data centre I'm located at? I'm not entirely sure of how the setup would work, I'm not unknowledged in networking, but this is a bit over my skills so far (but in order to learn, you've got to go out of your comfort zone, right?)

So from what I'm seeing, setting "Virtual" ips for one nic on the host OS, and then assigning the VMs those respective IPs would be the best route? Or would bridging be easier and still accomplish essentially the same end-result?

---

### Post by SeijiSensei on 2011-02-25
My VPS host, Linode, uses [Xen]("http://www.xen.org/").  I don't know how Xen manages IP addressing.  I do know my VM gets its IP via DHCP from some central server at boot.  My virtual interface has a (probably phony) MAC address, so I'm guessing they use that to assign static addresses.  

If you're thinking of hosting VMs, you probably need to do some deep study in both Xen and VMWare.  I don't think I'd try using Virtualbox for this task; it seems much more desktop oriented than the other two VM solutions.

It sounds to me like you need to do some lab work on a PC in your home or office.

---

